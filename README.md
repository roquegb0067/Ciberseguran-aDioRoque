# Desafio de Cibersegurança - DIO: Simulação de Phishing

Este repositório contém a documentação e os registros da execução do desafio prático de engenharia social da Digital Innovation One (DIO).

## 🛠️ Ambiente de Teste
* **Plataforma:** Android via Termux
* **Linguagem / Interpretador:** Python 3.14.6 e Bash

---

## 🛑 Dificuldades Técnicas e Solução de Problemas

### 1. Incompatibilidade de Dependências com o SET (Social-Engineer Toolkit)
Ao tentar instalar e configurar o **SET**, foram identificados impedimentos no ambiente do Termux:
* **Versão do Python:** O projeto exige versões do Python entre a `3.11` e inferiores à `3.14`. Como o ambiente Termux estava utilizando o Python `3.14.6`, ocorreram falhas de validação durante o build.
* **Alteração de Metadados:** Foi realizada a modificação dos limites de versão nos arquivos `requirements.txt` e `pyproject.toml` para contornar a restrição do instalador.
* **Falha de Compilação de Módulos Nativos:** A validação da versão foi ultrapassada, mas a instalação travou durante a compilação do pacote `pymssql` (dependência de banco de dados). O processo falhou devido à ausência de bibliotecas nativas de compilação em C (`FreeTDS` / `sqlfront.h`) e limitações de compilação cruzada no Termux.

---

## 💡 Solução Adotada: Migração para o Zphisher

Para garantir a conclusão do desafio dentro do escopo proposto e sem modificações invasivas no ambiente do sistema operacional, optou-se pela utilização do **Zphisher**.

* **Compatibilidade:** O Zphisher é desenvolvido inteiramente em Bash e PHP, o que o torna independente da versão do Python e nativamente compatível com a arquitetura do Termux.
* **Funcionalidade:** A ferramenta atende plenamente aos requisitos do laboratório, permitindo a simulação automatizada e a análise de templates de páginas de autenticação para fins estritamente educacionais e defensivos.

---


## 🛡️ Considerações de Segurança e Defesa

A análise prática desse tipo de vetor de ataque demonstra a importância da implementação de mecanismos defensivos robustos nas organizações:
* **Autenticação Passkey / WebAuthn:** Impede a captura efetiva de credenciais, pois a assinatura de autenticação é vinculada ao domínio oficial no navegador.
* **Gerenciadores de Senhas:** Evitam o preenchimento automático de credenciais em URLs que não correspondem exatamente ao serviço legítimo.
* **Conscientização do Usuário:** Treinamentos focados na verificação de domínios e identificação de links suspeitos.

