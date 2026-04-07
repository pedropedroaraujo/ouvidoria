# Sistema Integrado de Ouvidoria 📢

Projeto desenvolvido em **Python** e **MySQL** consistindo em uma solução digital, segura e organizada para a gestão de manifestações institucionais. O sistema substitui registros temporários por um armazenamento persistente, oferecendo um canal formal e rastreável.

## 👥 Equipe de Desenvolvimento
* Thiago Silva Menezes
* Danilo Silva Menezes
* Pedro Henrique Cabral de Araujo
* Mayke Willyan Silva Moura

---

## 🚀 Funcionalidades (CRUD na Prática)

O sistema cobre todo o ciclo de vida de uma manifestação, do cadastro à exclusão, com foco em segurança e usabilidade:

* **Create (Registro):** Cadastro rápido de manifestações categorizadas (Elogio, Sugestão ou Reclamação) com geração automática de protocolo (ID único).
* **Read (Consulta):** Listagem visual com formatação amigável e pesquisa direta pelo código da manifestação.
* **Update (Edição):** Menu inteligente que permite ao usuário escolher se deseja atualizar a Categoria ou a Descrição do registro.
* **Delete (Exclusão):** Remoção de registros protegida por trava de confirmação manual (`S/N`).
* **Métricas:** Resumo estatístico rápido com o total de reclamações ativas no banco de dados.

## 🛡️ Diferenciais de Segurança e Tratamento de Erros

O software foi construído para ser à prova de quebras inesperadas, implementando três camadas de proteção:
1. **Login Dinâmico:** As credenciais do banco de dados são solicitadas em tempo de execução, evitando senhas fixas ou expostas no código-fonte.
2. **Validação de Entrada (`.isdigit()`):** O sistema impede que letras sejam inseridas em menus numéricos, retornando avisos amigáveis em vez de encerrar abruptamente.
3. **Bloqueio de Textos Vazios (`.strip()`):** Validação rígida que recusa a inserção de descrições em branco antes mesmo do comando chegar ao banco de dados.
4. **Tratamento de Exceções (`try/except`):** Infraestrutura de banco de dados protegida contra falhas de conexão.

## 🏗️ Arquitetura do Sistema

O projeto segue um padrão de arquitetura modular, dividido em três camadas independentes para facilitar a manutenção e a clareza do código:

* 🖥️ **`appy.py` (Interface):** Responsável pela interação direta com o usuário, login dinâmico e exibição do menu principal.
* 🧠 **`FuncoesOuvidoria.py` (Regras de Negócio):** O núcleo lógico do sistema. Realiza as validações de entrada, formata as saídas visuais e empacota os dados de forma segura.
* ⚙️ **`operacoesbd.py` (Infraestrutura):** Camada de acesso ao banco de dados. Executa as operações SQL (Consultas, Inserções, Deleções) de maneira genérica e blindada.

---

## 💻 Como executar o projeto

### 1. Pré-requisitos
* Python 3.x instalado.
* Servidor MySQL instalado e rodando localmente (ou em nuvem).
* Biblioteca do conector MySQL para Python. Para instalar, rode no terminal:
  ```bash
  pip install mysql-connector-python