# 🎮 FriendsMod — Chat e Amigos no Minecraft

Um mod Fabric para Minecraft 1.20.1 que adiciona um sistema de amigos e chat em tempo real, como um WhatsApp dentro do jogo!

## ✨ Funcionalidades

- 💬 **Chat privado** com amigos em tempo real
- 👥 **Lista de amigos** com status online/offline
- 🔔 **Pedidos de amizade**
- 🌐 **Funciona em qualquer servidor** (incluindo launchers pirata)
- ⌨️ **Atalhos:** `Y` abre o chat, `U` abre a lista de amigos

---

## 🛠️ Como Compilar o Mod

### Pré-requisitos
- Java 17+ ([Baixar aqui](https://adoptium.net/))
- Git

### Passos

```bash
# 1. Clone o projeto
git clone https://github.com/seuuser/friendsmod
cd friendsmod

# 2. Compile
./gradlew build          # Linux/Mac
gradlew.bat build        # Windows

# O .jar estará em: build/libs/friendsmod-1.0.0.jar
```

---

## 🖥️ Configurar o Servidor Backend

O mod precisa de um servidor Node.js para funcionar. Você pode hospedar gratuitamente no **Railway** ou **Render**.

### Rodar localmente (para testes)

```bash
cd server
npm install
npm start
# Servidor rodando em ws://localhost:8080
```

### Hospedar no Railway (GRÁTIS)

1. Acesse [railway.app](https://railway.app) e crie uma conta
2. Clique em "New Project" → "Deploy from GitHub"
3. Suba a pasta `server/` no GitHub e conecte
4. Railway vai gerar uma URL tipo: `wss://seu-app.railway.app`
5. **Copie essa URL e cole em `FriendsMod.java`:**
   ```java
   public static final String SERVER_URL = "wss://seu-app.railway.app";
   ```
6. Recompile o mod com `./gradlew build`

---

## 📦 Publicar no Modrinth

1. Crie uma conta em [modrinth.com](https://modrinth.com)
2. Clique em **"Create a project"**
3. Preencha:
   - **Name:** FriendsMod
   - **Project type:** Mod
   - **Summary:** "Chat e sistema de amigos no Minecraft!"
   - **Description:** Explique as funcionalidades
4. Na aba **"Versions"**, clique em "Upload a version"
5. Faça upload do arquivo `build/libs/friendsmod-1.0.0.jar`
6. Configure:
   - **Version number:** 1.0.0
   - **Loaders:** Fabric
   - **Game versions:** 1.20.1
   - **Dependencies:** Fabric API
7. Publique! ✅

---

## 🎮 Como Instalar (para usuários)

1. Instale o **Fabric Loader** em [fabricmc.net](https://fabricmc.net)
2. Instale o **Fabric API** no Modrinth
3. Baixe o **FriendsMod** e coloque na pasta `mods/`
4. Inicie o Minecraft com o perfil Fabric

**Funciona com launcher pirata?** Sim! Qualquer launcher que suporte Fabric funciona (SKlauncher, TLauncher, ATLauncher, Modrinth App, etc.)

---

## 📁 Estrutura do Projeto

```
friendsmod/
├── build.gradle              # Configuração de build
├── gradle.properties         # Versões
├── src/main/java/com/friendsmod/
│   ├── FriendsMod.java       # Classe principal
│   ├── FriendsModClient.java # Inicialização do cliente + keybinds
│   ├── data/
│   │   ├── ChatMessage.java  # Modelo de mensagem
│   │   └── FriendData.java   # Modelo de amigo
│   ├── gui/
│   │   ├── ChatScreen.java   # Tela de chat (tecla Y)
│   │   └── FriendsScreen.java # Tela de amigos (tecla U)
│   ├── mixin/
│   │   └── TitleScreenMixin.java # Conecta ao server na tela inicial
│   └── network/
│       └── FriendsWebSocketClient.java # Comunicação WebSocket
└── server/
    ├── server.js             # Servidor Node.js
    └── package.json
```

---

## 🔧 Personalizar

- **Mudar teclas:** Edite `FriendsModClient.java` (GLFW.GLFW_KEY_Y / GLFW.GLFW_KEY_U)
- **Mudar servidor:** Edite `FriendsMod.java` → `SERVER_URL`
- **Adicionar persistência:** No `server.js`, substitua o `Map` por SQLite ou MongoDB

---

## ⚠️ Limitações Atuais

- Sem persistência de mensagens (se o servidor reiniciar, mensagens somem) — adicione um banco de dados para resolver
- Sem criptografia (para produção, use wss:// e adicione autenticação)
- Sem suporte a grupos (apenas chat 1:1 por enquanto)

---

## 📄 Licença

MIT — faça o que quiser, mas dê créditos! 😊
