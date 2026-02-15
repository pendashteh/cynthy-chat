# 🌸 Cynthy's AI - Local Server Interface

<div align="center">

![Cynthy's AI Banner](https://img.shields.io/badge/Cynthy's_AI-シンシーのAI-1a237e?style=for-the-badge)
[![License](https://img.shields.io/badge/license-MIT-blue.svg?style=for-the-badge)](LICENSE)
[![Status](https://img.shields.io/badge/status-active-success.svg?style=for-the-badge)](https://github.com/yourusername/cynthys-ai)

*A beautiful, Japanese-inspired web interface for your local AI server*

[Features](#features) • [Quick Start](#quick-start) • [Configuration](#configuration) • [Troubleshooting](#troubleshooting)

</div>

---

## ✨ Features

### 🎨 **Beautiful Design**
- Japanese-inspired navy blue aesthetic (和風)
- Smooth animations and transitions
- Clean, minimal interface with zen philosophy
- Responsive design for desktop and mobile

### 🚀 **Powerful Functionality**
- **Real-time Streaming**: Watch AI responses appear word-by-word
- **Persistent Conversations**: Chat history saved locally across sessions
- **Model Selection**: Browse and switch between available models
- **Connection Diagnostics**: Built-in troubleshooting tools
- **Configuration Persistence**: Settings saved in browser localStorage

### 🔧 **Developer-Friendly**
- OpenAI-compatible API support
- Works with Jan.AI, LM Studio, LocalAI, and more
- Detailed connection diagnostics
- CORS-enabled
- No backend required - pure HTML/CSS/JavaScript

---

## 🎯 Quick Start

### Prerequisites
- A local AI server running (Jan.AI, LM Studio, etc.)
- Modern web browser (Chrome, Firefox, Safari, Edge)

### Installation

1. **Download the HTML file**
```bash
   curl -O https://raw.githubusercontent.com/yourusername/cynthys-ai/main/index.html
```

2. **Open in your browser**
```bash
   # On Mac
   open index.html
   
   # On Linux
   xdg-open index.html
   
   # On Windows
   start index.html
```

3. **Configure your server**
   - Enter your server's IP address (e.g., `localhost` or `192.168.1.100`)
   - Enter the port (e.g., `1337`)
   - Add your API key if required
   - Click "🔍 Test Connection"

4. **Start chatting!**
   - Enable streaming for real-time responses
   - Select your preferred model
   - Type your message and hit Enter

---

## ⚙️ Configuration

### Server Settings

| Setting | Description | Example |
|---------|-------------|---------|
| **IP Address** | Server hostname or IP | `localhost`, `192.168.1.100` |
| **Port** | Server port number | `1337`, `8000`, `1234` |
| **API Key** | Optional authentication key | `sk-...` |
| **Streaming** | Enable word-by-word responses | ✅ Recommended |

### Supported Servers

- ✅ **Jan.AI** - Local AI server with multiple models
- ✅ **LM Studio** - Cross-platform desktop app
- ✅ **LocalAI** - OpenAI-compatible local inference
- ✅ **Ollama** - Run Llama 2, Code Llama, and more
- ✅ **Text Generation Web UI** - Gradio-based UI
- ✅ Any OpenAI-compatible API endpoint

---

## 🔍 Troubleshooting

### Connection Issues

#### "Connection Failed" Error

**Problem**: Can't connect to server at `192.168.x.x:1337`

**Solutions**:
1. Check if server is running: `curl http://localhost:1337/v1/models`
2. Verify you're on the same WiFi network
3. Check firewall settings on both machines
4. Try using `localhost` if running on the same machine

#### "Invalid Host Header" (Jan.AI specific)

**Problem**: Getting 403 Forbidden with Jan.AI

**Solution**: This is a [known Jan.AI bug](https://github.com/janhq/jan/issues/7345). Use one of these workarounds:

**Option 1: Use nginx proxy** (Recommended for LAN access)
```nginx
server {
    listen 8080;
    location / {
        proxy_pass http://localhost:1337;
        proxy_set_header Host localhost;
    }
}
```

**Option 2: Configure Jan's trusted hosts**
- In Jan.AI settings, add `*` or `192.168.*.*` as trusted hosts

**Option 3: Use on the same machine**
- Access via `http://localhost:1337` directly

#### Testing with curl
```bash
# Test models endpoint
curl -H "Authorization: Bearer $KEY" http://localhost:1337/v1/models

# Test chat endpoint
curl -X POST http://localhost:1337/v1/chat/completions \
  -H "Authorization: Bearer $KEY" \
  -H "Content-Type: application/json" \
  -d '{"model":"gpt-3.5-turbo","messages":[{"role":"user","content":"Hi"}]}'
```

### Streaming Not Working

If streaming doesn't work:
1. Disable streaming in settings (uncheck the box)
2. Check if your server supports streaming
3. Verify your server's streaming implementation

### Chat History

**Clear history**: Open browser console and run:
```javascript
localStorage.removeItem('cynthyAI_history');
localStorage.removeItem('cynthyAI_config');
location.reload();
```

---

## 🎨 Design Philosophy

Cynthy's AI embraces **Japanese aesthetic principles**:

- **侘寂 (Wabi-Sabi)**: Beauty in simplicity and imperfection
- **間 (Ma)**: Negative space and breathing room
- **引き算 (Hikizan)**: Subtraction - removing the unnecessary
- **和 (Wa)**: Harmony in color and composition

The navy blue color scheme (藍色 - Ai-iro) represents:
- 🌊 Depth and stability
- 🌙 Calm and professionalism  
- ⚡ Technology and innovation

---

## 🛠️ Technical Details

### Technology Stack
- **Frontend**: Pure HTML5, CSS3, JavaScript (ES6+)
- **Storage**: Browser localStorage
- **API**: OpenAI-compatible REST API
- **Streaming**: Server-Sent Events (SSE)

### Browser Compatibility
- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+

### Features
- Real-time streaming with SSE
- Conversation persistence
- Model management
- Connection diagnostics
- Error handling with friendly messages
- Responsive design

---

## 📝 API Endpoints Used
```
GET  /v1/models              # List available models
POST /v1/chat/completions    # Send chat messages
```

### Request Format
```json
{
  "model": "gpt-3.5-turbo",
  "messages": [
    {"role": "user", "content": "Hello!"}
  ],
  "stream": true,
  "max_tokens": 2000,
  "temperature": 0.7
}
```

---

## 🤝 Contributing

Contributions are welcome! Feel free to:

- 🐛 Report bugs
- 💡 Suggest features
- 🔧 Submit pull requests
- 📖 Improve documentation

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- Inspired by Japanese design aesthetics
- Built for the [Jan.AI](https://jan.ai) community
- Compatible with OpenAI API standards

---

## 💬 Support

Having issues? Check out:

- [GitHub Issues](https://github.com/yourusername/cynthys-ai/issues)
- [Jan.AI Documentation](https://jan.ai/docs)
- [Troubleshooting Guide](#troubleshooting)

---

<div align="center">

**Made with 愛 (love) for the local AI community**

シンシーのAI © 2026

[⬆ Back to Top](#-cynthys-ai---local-server-interface)

</div>
