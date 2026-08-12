# ChapaPrime

**ChapaPrime** é um app desktop para **planejamento de corte e dobra de chapas**.  
Foco inicial em **corte 1D** (no comprimento), com cálculo de **BLANK** e **peso**, otimização de cortes considerando **kerf / margem / folga**, **pré-visualização técnica** (chapa com cotas, margens, folgas e rótulos) e **exportação profissional** em **PDF** e **PNG**.

---

---

## 📌 Status

Protótipo funcional, desenvolvimento pausado. O Planner 1D (cálculo, otimização, 
pré-visualização e exportação) opera de ponta a ponta. O módulo de OP/dobras ficou 
incompleto.

Nasceu de um problema real: trabalhei três anos em produção industrial e o 
planejamento de corte era feito manualmente, com desperdício de material. Construí 
a ferramenta para resolver isso. Parei o desenvolvimento ao priorizar outro projeto.

Mantenho o repositório público porque o Planner demonstra o cálculo de BLANK, a 
otimização com kerf e a geração de desenho técnico — que era o núcleo do problema.

Construído com apoio de IA para geração de código, em 2025, antes dos agentes de programação atuais. Eu definia o problema, montava a estrutura, integrava e depurava.

## ✨ Recursos

- **Planner 1D**: insira a composição por **Texto** (`1x600, 2x400, 3x240`) ou **Tabela** (Qtd × Comprimento).
- Parâmetros de processo: **Kerf**, **Margem**, **Folga**.
- **Desenho técnico** interativo:
  - Chapa com **cotas** (comprimento), **margens** (início/fim), **folgas** entre peças e **kerf**.
  - **Camadas** liga/desliga (Grade, Cotas, Margens, Rótulos), **Zoom +/−** e **Ajustar à tela**.
- **Resumo automático**: peças, chapas, **aproveitamento (%)** e **sobra total (mm)**.
- **Exportar**:
  - **PDF (A4)** do layout (uso de ReportLab).
  - **PNG** do layout (fundo transparente) para catálogos/WhatsApp.
- **Interface Dark** e responsiva, pensada para **chão de fábrica**.

---

## 🧰 Tecnologias utilizadas

- **Python 3.12+**
- **PySide6 (Qt)**: UI desktop, QGraphicsView/Scene para o desenho técnico.
- **ReportLab**: geração de **PDF** (A4).
- **Dataclasses / typing**: modelo de dados tipado.
- **Regex (re)**: parsing robusto da composição em texto.
- (Opcional) **venv** para isolamento do ambiente.

> O app roda **100% local** (sem dependências de nuvem).

---

## 🗂️ Estrutura

app/
├─ main.py # ponto de entrada
├─ shell/
│ └─ main_window.py # janela principal (tabs)
├─ tabs/
│ ├─ planner/ # Planner (corte 1D)
│ │ ├─ view.py # UI da aba
│ │ └─ controller.py # lógica: parse, planejamento, desenho, export
│ └─ op/ # OP (dobras) – em evolução
│ ├─ view.py
│ └─ controller.py
└─ ui/ # estilos/ícones (opcional)


---

## 🚀 Como rodar

1. **Clone**
```bash
git clone https://github.com/sandervanzo/ChapaPrime.git
cd ChapaPrime
