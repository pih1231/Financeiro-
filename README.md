# 💸 NeoFlow — Gestão Financeira Pessoal

> Um aplicativo web moderno, elegante e funcional para controle das suas finanças pessoais. Desenvolvido com HTML, CSS e JavaScript puro — sem frameworks, sem backend obrigatório — e pronto para hospedar no **Vercel** ou rodar localmente com **XAMPP**.

---

## ✨ O que é o NeoFlow?

O **NeoFlow** é um sistema de gestão financeira pessoal com design premium (glassmorphism + neon), totalmente responsivo, que roda diretamente no navegador. Ele permite registrar receitas e despesas, criar metas de poupança ("Caixinhas"), visualizar gráficos de gastos e obter insights inteligentes sobre sua saúde financeira.

---

## 🚀 Funcionalidades

### 📊 Dashboard
- **Cards de resumo financeiro** com Saldo, Receitas e Despesas do mês ou do ano
- **Filtro temporal** — alterna entre visão Mensal e Anual com seletor de mês/ano
- **Projeção anual** de economia com base nos meses já transcorridos
- **Formulário de lançamento** com:
  - Seletor visual de tipo: Receita 🟢 ou Despesa 🔴
  - Campo de valor com suporte a formato brasileiro (R$ 1.234,56)
  - Campo de tópico/categoria com **autocomplete inteligente**
  - Campo de data com **fuso horário local** (sem bug de UTC)
  - Campo de descrição livre
- **Histórico de lançamentos** com:
  - Ordenação por data (mais recentes primeiro)
  - Filtro por tipo (Todos / Receitas / Despesas)
  - Edição inline com highlight visual no item sendo editado
  - Exclusão com diálogo de confirmação animado
  - Ícones dinâmicos por categoria (alimentação, transporte, saúde, etc.)

### 🏦 Caixinhas (Metas de Poupança)
- Criação de metas com nome e valor objetivo
- **Barra de progresso neon** mostrando o percentual guardado
- Ajuste rápido de saldo: depositar ou retirar valor diretamente no card
- Edição e exclusão de metas com diálogo de confirmação

### 📈 Insights & Análise
- **Gráfico de rosca** (Chart.js) com distribuição de gastos por categoria no ano
- **Tópico mais frequente**: categoria com mais lançamentos de despesa
- **Maior impacto no orçamento**: categoria com maior valor acumulado
- **Saúde financeira**: avalia a proporção gasto/receita com alertas e dicas

### 🎨 Design & UX
- Tema **Dark** (padrão) e **Light** com transição suave
- Glassmorphism com backdrop-filter e cards translúcidos
- Cores neon: Cyan, Pink, Purple e Green
- Tipografia premium: **Plus Jakarta Sans** + **Outfit** (Google Fonts)
- Ícones vetoriais: **Lucide Icons**
- Layout adaptável: Automático / Forçar Desktop / Forçar Mobile
- **Navegação mobile** com barra inferior fixa
- **Toast notifications** animadas (sucesso, erro, info, aviso)
- **Diálogo de confirmação** customizado com animação de pulse no ícone

---

## 🗂️ Estrutura do Projeto

```
financeiro/
├── index.html            # App completo (HTML + CSS + JS em um único arquivo)
├── api.php               # API PHP para persistência no XAMPP (opcional)
├── financeiro_data.json  # Arquivo de dados do servidor (inicia vazio)
└── README.md             # Esta documentação
```

---

## 💾 Persistência de Dados

O NeoFlow funciona em **dois modos de armazenamento**:

| Ambiente | Leitura | Escrita |
|---|---|---|
| **Vercel** (estático) | `localStorage` | `localStorage` |
| **XAMPP** (PHP local) | `api.php` → JSON | `api.php` + `localStorage` |

- Os dados são salvos no `localStorage` do navegador com a chave versionada `neoflow_v1_*`
- Chaves legadas de versões anteriores são removidas automaticamente na inicialização
- **Novos usuários sempre começam com valores zerados (R$ 0,00)**
- Cada dispositivo/navegador tem seu próprio conjunto de dados

---

## 🌐 Como hospedar no Vercel

1. Faça o fork ou clone deste repositório no GitHub
2. Acesse [vercel.com](https://vercel.com) e conecte seu repositório
3. Clique em **Deploy** — nenhuma configuração extra necessária
4. O app estará disponível em `https://seu-projeto.vercel.app`

> O `api.php` será ignorado no Vercel (sem suporte a PHP). O app usa automaticamente o `localStorage` como fonte de dados.

---

## 🖥️ Como rodar localmente com XAMPP

1. Copie a pasta `financeiro/` para `C:\xampp\htdocs\`
2. Inicie o **Apache** no painel do XAMPP
3. Acesse `http://localhost/financeiro/` no navegador
4. Os dados serão salvos em `financeiro_data.json` via `api.php`

---

## 🛠️ Tecnologias Utilizadas

| Tecnologia | Versão | Uso |
|---|---|---|
| HTML5 | — | Estrutura da aplicação |
| CSS3 | — | Design, glassmorphism, animações |
| JavaScript (ES2020) | — | Lógica, estado, CRUD, renderização |
| [Chart.js](https://www.chartjs.org/) | CDN latest | Gráfico de distribuição de gastos |
| [Lucide Icons](https://lucide.dev/) | CDN latest | Ícones vetoriais SVG |
| [Google Fonts](https://fonts.google.com/) | — | Plus Jakarta Sans + Outfit |
| PHP 7+ | — | API opcional para XAMPP |
| localStorage | — | Persistência no Vercel |

---

## 📋 Funcionalidades Técnicas

- **Event Delegation** nos botões do histórico (compatível com `lucide.createIcons()`)
- **Autocomplete** de categorias com histórico do usuário + sugestões padrão
- **Detecção de ambiente** (Vercel vs XAMPP) via `Content-Type` da resposta da API
- **Escape de HTML** em todos os dados do usuário (prevenção de XSS)
- **Fuso horário local** na data padrão do formulário (evita bug de UTC)
- **Estado de edição** rastreado no objeto `state.editingId` com highlight visual
- **Filtro preservado** ao re-renderizar a lista após salvar/excluir
- **Formulário auto-resetado** ao excluir um item que estava em edição

---

## 📸 Telas

| Dashboard | Caixinhas | Insights |
|---|---|---|
| Cards de saldo + formulário + histórico | Grid de metas com progresso neon | Gráfico de rosca + análise inteligente |

---

## 👨‍💻 Desenvolvido por

**NeoFlow** foi desenvolvido como um projeto de gestão financeira pessoal, focado em design moderno e usabilidade em qualquer dispositivo.

---

*"Controle suas finanças com estilo."* ✨
