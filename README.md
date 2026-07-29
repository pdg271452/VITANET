# VITANET
Prerequisites & System Requirements
Before running or training VitaNet, ensure your system meets the hardware and driver specifications required for deep learning workloads.
Hardware Requirements
Component,Minimum Specification,Recommended (Training & Fine-Tuning)
CPU:-8-core x86-64 Processor,16+ core AMD Ryzen / Intel Core i7/i9 or Xeon
RAM:-16 GB,32 GB – 64 GB
GPU:-"NVIDIA GPU with 8 GB VRAM (e.g., RTX 3060)","NVIDIA GPU with 16+ GB VRAM (e.g., RTX 3090, RTX 4090, or A100)"
Storage:-20 GB available SSD space,100+ GB NVMe SSD (for dataset caching)

Drivers & Software Dependencies
Operating System: Linux (Ubuntu 20.04/22.04 LTS recommended), macOS (Apple Silicon supported for MPS inference), or Windows 11 with WSL2.
Anaconda / Miniconda: Python package and environment manager (Python 3.10+ target).
NVIDIA Driver: Version >= 525.60.13 (for CUDA 12.1 support).
CUDA Toolkit & cuDNN: CUDA 12.1 and cuDNN 8.9+ (managed automatically via PyTorch conda installation).

Anaconda Environment Setup
Using Conda is strongly recommended to isolate dependencies and handle C++ libraries (such as OpenCV, CUDA binaries, and ONNX Runtime) cleanly.

1. Install Conda / Miniconda
If you do not have Anaconda or Miniconda installed:
# Download and run the Miniconda installer (Linux)
curl -O https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh

2. Create and Activate the Conda Environment
Create a dedicated environment named vitanet with Python 3.10:
# Create the environment
conda create -n vitanet python=3.10 -y

# Activate the environment
conda activate vitanet

3. Install PyTorch with CUDA Acceleration
Install PyTorch, TorchVision, and dependencies built against CUDA 12.1:
# Install PyTorch GPU version via Conda
conda install pytorch torchvision torchaudio pytorch-cuda=12.1 -c pytorch -c nvidia -y

For CPU-Only Environments (Inference / Local Testing):

Bash
conda install pytorch torchvision torchaudio cpuonly -c pytorch -y

4.Install Core Project Dependencies
Install the remaining Python packages using pip inside your activated Conda environment:

Bash
# Clone the repository (if not already done)
git clone https://github.com/your-org/vitanet.git
cd vitanet

# Install dependencies from requirements.txt
pip install -r requirements.txt

5.Verify the GPU Setup
Run this inline command to ensure PyTorch detects your GPU correctly:

Bash
python -c "import torch; print('CUDA Available:', torch.cuda.is_available()); print('Device Name:', torch.cuda.get_device_name(0) if torch.cuda.is_available() else 'CPU')"
Expected Output:

Plaintext
CUDA Available: True
Device Name: NVIDIA GeForce RTX 3090 (or your GPU model)
