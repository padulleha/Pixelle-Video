# Pixelle-Video

A fork of [AIDC-AI/Ovis](https://github.com/AIDC-AI/Pixelle-Video) — an open-source video generation and understanding model.

## Overview

Pixelle-Video is a multimodal video model designed for high-quality video generation, editing, and understanding tasks. This fork extends the original with additional features, optimizations, and developer tooling.

## Features

- 🎬 **Video Generation** — Generate high-quality videos from text prompts
- 🖼️ **Image-to-Video** — Animate still images with natural motion
- 🔍 **Video Understanding** — Analyze and describe video content
- ⚡ **Optimized Inference** — Quantization and batching support
- 🐳 **Docker & DevContainer** — Ready-to-use containerized environments

## Quick Start

### Using Docker

```bash
docker build -t pixelle-video .
docker run --gpus all -p 7860:7860 pixelle-video
```

### Using DevContainer

Open this repository in VS Code and select **Reopen in Container** when prompted. The environment will be set up automatically.

### Manual Installation

```bash
# Clone the repository
git clone https://github.com/your-org/Pixelle-Video.git
cd Pixelle-Video

# Create a virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

## Usage

### Text-to-Video

```python
from pixelle_video import PixelleVideoPipeline

pipeline = PixelleVideoPipeline.from_pretrained("pixelle-video-base")
video = pipeline(
    prompt="A serene mountain landscape with flowing waterfalls at sunset",
    num_frames=49,
    height=480,
    width=720,
)
video.save("output.mp4")
```

### Image-to-Video

```python
from pixelle_video import PixelleVideoPipeline
from PIL import Image

pipeline = PixelleVideoPipeline.from_pretrained("pixelle-video-base")
image = Image.open("input.jpg")
video = pipeline(
    image=image,
    prompt="Gentle breeze moving through the trees",
    num_frames=49,
)
video.save("output.mp4")
```

### Gradio Demo

```bash
python app.py
```

Then open `http://localhost:7860` in your browser.

## Requirements

- Python 3.10+
- CUDA 12.1+ (for GPU inference)
- 24GB+ VRAM recommended (16GB with quantization)

## Model Weights

Model weights are available on Hugging Face:

| Model | Parameters | VRAM | Link |
|-------|-----------|------|------|
| pixelle-video-base | 5B | 24GB | [🤗 Hub](#) |
| pixelle-video-base-int8 | 5B | 16GB | [🤗 Hub](#) |

## Configuration

See [`configs/`](configs/) for available configuration options.

## Contributing

Contributions are welcome! Please read our [Contributing Guide](CONTRIBUTING.md) and submit pull requests to our repository.

1. Fork the repository
2. Create your feature branch (`git checkout -b feat/amazing-feature`)
3. Commit your changes (`git commit -m 'feat: add amazing feature'`)
4. Push to the branch (`git push origin feat/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the Apache 2.0 License — see the [LICENSE](LICENSE) file for details.

## Acknowledgements

- [AIDC-AI](https://github.com/AIDC-AI) for the original Pixelle-Video model
- [Hugging Face Diffusers](https://github.com/huggingface/diffusers) for the pipeline infrastructure
- The open-source AI community

## Citation

```bibtex
@misc{pixellevideo2024,
  title={Pixelle-Video: Open-Source Video Generation Model},
  author={AIDC-AI},
  year={2024},
  url={https://github.com/AIDC-AI/Pixelle-Video}
}
```
