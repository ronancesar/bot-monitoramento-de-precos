# 🛒 Super Monitor Bot - Rastreador de Preços

Este é um sistema completo de monitoramento de preços (Amazon e Mercado Livre) integrado ao Telegram. O projeto foi desenvolvido com foco em arquitetura modular, persistência de dados e evasão de sistemas anti-bot.

O bot permite que usuários cadastrem produtos para vigiar, recebam alertas de promoção em tempo real e gerenciem sua lista de desejos, tudo através de uma interface de chat.

# Funcionalidades

-   **Interface via Telegram:** Comandos interativos (`/vigiar`, `/lista`, `/remover`) para gerenciar produtos.
-   **Scraper Invisível (Stealth):** Utiliza **Playwright** com técnicas de camuflagem para simular navegação humana e evitar bloqueios (Captchas/Soft-blocks) da Amazon.
-   **Automação Inteligente:** Sistema de **JobQueue** que verifica preços automaticamente a cada 30 minutos em segundo plano.
-   **Persistência de Dados:** Uso de **SQLite** para salvar usuários e produtos, garantindo que nenhum dado seja perdido se o bot reiniciar.
-   **Arquitetura Modular:** Código organizado em camadas (`database`, `scraper`, `bot`, `monitor`) seguindo boas práticas de engenharia de software (Separation of Concerns).
-   **Assíncrono:** Utiliza `asyncio` para garantir que o bot continue respondendo mensagens enquanto o scraper navega na internet.

# Tecnologias Utilizadas

-   **Linguagem:** Python 3.10+
-   **Automação Web:** Playwright (Async API)
-   **Interface:** Python-telegram-bot (v20+)
-   **Banco de Dados:** SQLite3
-   **Parsing:** BeautifulSoup4
-   **Gerenciamento de Ambiente:** Dotenv

# Estrutura do Projeto

```text
super-monitor-bot/
├── src/
│   ├── bot.py          # Interface do Telegram e Agendador de Tarefas
│   ├── database.py     # Camada de persistência (CRUD SQLite)
│   ├── scraper.py      # Robô de navegação (Playwright + BeautifulSoup)
│   └── monitor.py      # Lógica de verificação manual (opcional)
├── .env                # Variáveis de ambiente (Token)
├── requirements.txt    # Dependências do projeto
└── README.md           # Documentação
