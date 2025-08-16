

# 🎬 ZeroScope AI Video Generator

Text-to-video generation using the open-source **ZeroScope v2 576w diffusion model** with a clean web interface. Designed for Colab (GPU recommended) or local installs (demo mode). Convert text prompts into unique AI-generated video clips—no proprietary APIs, just open-source AI!

***

## ⭐ Features

- **ZeroScope v2 576w (Hugging Face):** state-of-the-art open-source text-to-video
- **Web interface:** Easy prompt → video workflow, one-click generation
- **Colab compatibility:** Zero config, auto public link in Colab
- **GPU acceleration:** Fast generation on T4/V100/A100 (or slow on CPU)
- **CPU fallback/demo mode:** Preview the system even without a GPU
- **REST API:** Easily integrate or automate video generation
- **No vendor lock-in:** 100% open-source stack, no API keys needed for public models

***




***

## 🗂️ Why This Structure?

- **Colab-first:** Anyone can demo with a GPU, no setup or configuration pains.
- **Self-contained web & API:** All in FastAPI, simple extension/hosting anywhere.
- **GPU detection/fallback:** Best quality possible for available hardware.
- **Minimal external dependencies:** Fast, reproducible, open.
- **Real reproducible demo:** No marketing hype, demo mode for full transparency.

***

## 🚦 Quick Start (Colab)

1. **Open this project in [Google Colab](https://colab.research.google.com/):**
2. **Change runtime to GPU:**  
   `Runtime` → `Change runtime type` → Select `T4 GPU`
3. **Run all cells.**  
   - Model loads (~3–5min on T4)  
   - A public web link is displayed—click to launch the app!
4. **Enter a prompt, generate your video, and watch/download the result.**

***

## 💻 System Requirements

| Mode           | Python | RAM     | GPU      | Notes                       |
|----------------|--------|---------|----------|-----------------------------|
| Demo/CPU       | 3.8+   | 4GB     | None     | Slow, low-res video         |
| AI (GPU, best) | 3.8+   | 16GB+   | 16GB+ VRAM (T4/V100) | Fast, hi-res video    |

- *Minimum*: Python 3.8+, 4GB RAM, for demo mode only
- *Recommended*: Python 3.8+, 16GB+ RAM, NVIDIA GPU (16GB VRAM or more)

***

## 🛠️ Dependencies

All dependencies are installed automatically in Colab, or run:
```bash
pip install fastapi uvicorn diffusers[torch] torch imageio moviepy
```

***

## 🔥 Usage Guide

### Web Interface
- Open the generated public URL or local app
- Type a descriptive prompt (see built-in examples)
- Click “Generate”
- Wait for video (2–4min on GPU, longer for CPU/demo)
- Watch or download the result!

### API (For Developers)
- `POST /generate-video`  
  - JSON: `{"prompt": "your text prompt", "duration": 3}`
- `GET /video/{video_id}`  
  - Download or stream your generated video

***

## 📝 Example Prompts

- “A butterfly landing on a sunflower”
- “Colorful paint drops splashing in water”
- “A cute cat playing with yarn”
- “Rain drops falling on green leaves”

***

## ⚙️ Settings & Configuration

| Setting       | GPU (Best)     | CPU (Demo)   |
|---------------|---------------|--------------|
| Resolution    | 576x320       | 320x256      |
| Frames      | 16            | 8–12         |
| Steps         | 20            | 10–15        |
| Wait time     | 2–5min        | 10–15min     |

Change these in the code for different speed/quality tradeoffs.

***

## 🧑🔬 Troubleshooting

- **CUDA out of memory:**  
  Lower `num_frames`, resolution, or inference steps in config.
- **Model not loading:**  
  Check internet, restart session.
- **Web page not loading:**  
  Wait 30 seconds after startup; check the public/local URL.
- **Video takes too long:**  
  Use a shorter or simpler prompt, run on GPU, or try demo mode.

***

## 🚧 How It Works (How + Why)

- **GPU/CPU detection:**  
  Loads the best available version of ZeroScope at runtime.
- **Optimizations:**  
  XFormers and attention/vae slicing for efficiency where supported.
- **Colab (Threaded server):**  
  Runs FastAPI server in background, auto-generates preview link.
- **REST API + Web UI:**  
  Clean HTML-only frontend for fast loading and UX, plus well-documented API routes.
- **Open-source all the way:**  
  No paid API, Hugging Face open models, nothing hidden—just reproducible, transparent results.
- **Demo mode fallback:**  
  Lets you see web UI and basic workflow without a GPU.

***


