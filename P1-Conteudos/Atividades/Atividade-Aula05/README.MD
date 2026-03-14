### README.md

---

### Descrição
Este repositório contém a solução da **Atividade Aula 05 — Testes Automatizados com Jest**. O objetivo é implementar testes unitários com Jest, integrar a execução dos testes no pipeline do GitHub Actions e demonstrar o comportamento do CI quando os testes passam e quando falham. 


### Estrutura do repositório
**Pasta da atividade**
- **P1-Conteudos/Atividades/AtividadeAula05/** — local onde devem ficar o PDF e este README.  
**Arquivos principais**
- **IEC-Atividade-Aula05.pdf** — PDF da atividade entregue.   
- **tests/** — arquivos de teste (ex.: `soma.test.js`, `alerta.test.js`).  
- **package.json** — scripts e dependências de desenvolvimento.  
- **.github/workflows/ci.yml** — workflow do GitHub Actions para rodar ESLint e Jest. 

---

### Instalação e execução local
**Instalar dependências**
```bash
npm install
npm install jest --save-dev
```

**Adicionar script de teste** no `package.json` (se ainda não existir):
```json
"scripts": {
  "test": "jest"
}
```

**Rodar os testes**
```bash
npm test
```

**Exemplos de testes**
- `tests/soma.test.js`  
- `tests/alerta.test.js`  
Os testes devem passar quando as funções estiverem implementadas corretamente. 

---

### Integração contínua GitHub Actions
O pipeline deve executar em pushes e pull requests para a branch **dev**, fazendo checkout, configurando Node.js (versão 18), instalando dependências, rodando ESLint e executando Jest. Exemplo de job para `.github/workflows/ci.yml`:

```yaml
name: CI com ESLint e Testes

on:
  push:
    branches: [ dev ]
  pull_request:
    branches: [ dev ]

jobs:
  lint-and-test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout do repositório
        uses: actions/checkout@v4

      - name: Configurar Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '18'

      - name: Instalar dependências
        run: npm install

      - name: Rodar ESLint
        run: npx eslint .

      - name: Rodar Jest
        run: npm test
```
Após o commit, verifique a aba **Actions** no GitHub para confirmar que o pipeline executa ESLint e Jest. 

---

### Instruções de entrega
1. Exporte/salve o arquivo com o nome **IEC-Atividade-Aula05.pdf**.   
2. Coloque o PDF e este `README.md` em `P1-Conteudos/Atividades/AtividadeAula05/`.  
3. Faça commit e push para o repositório da disciplina `FATEC-JCR-4DSM-IEC-2026-1-seunome`.  
4. Copie o link do PDF no GitHub e cole como comentário no card **IEC-Atividade-Aula05** do Kanban da disciplina.   
5. No seu Kanban pessoal do repositório, mova o card **IEC-Atividade-Aula05** para a coluna **Entregue**. 

teste