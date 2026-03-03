# envs

(torch) violi@Paganini:/mnt/c/Users/violi$ nvidia-smi
    Tue Mar  3 14:06:40 2026
    +-----------------------------------------------------------------------------------------+
    | NVIDIA-SMI 580.112                Driver Version: 581.95         CUDA Version: 13.0     |
    +-----------------------------------------+------------------------+----------------------+
    | GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
    | Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
    |                                         |                        |               MIG M. |
    |=========================================+========================+======================|
    |   0  NVIDIA GeForce RTX 5090 ...    On  |   00000000:01:00.0  On |                  N/A |
    | N/A   44C    P8             16W /  175W |    4545MiB /  24463MiB |      2%      Default |
    |                                         |                        |                  N/A |
    +-----------------------------------------+------------------------+----------------------+
    
    +-----------------------------------------------------------------------------------------+
    | Processes:                                                                              |
    |  GPU   GI   CI              PID   Type   Process name                        GPU Memory |
    |        ID   ID                                                               Usage      |
    |=========================================================================================|
    |  No running processes found                                                             |
    +-----------------------------------------------------------------------------------------+

UserWarning:  NVIDIA GeForce RTX 5090 Laptop GPU with CUDA capability sm_120 is not compatible with the current PyTorch installation. 
The current PyTorch install supports CUDA capabilities sm_50 sm_60 sm_61 sm_70 sm_75 sm_80 sm_86 sm_90.

So I had to install pytorch as follows:

## torch
As of 3/3/26:

1. Create and activate environment
conda create -n torch python=3.11
conda activate torch

2. Install everything except PyTorch via conda
conda install ipykernel jupyter scikit-learn matplotlib pandas

3. Install PyTorch nightly via pip (for sm_120 support)
pip install --pre torch torchvision torchaudio \
  --index-url https://download.pytorch.org/whl/nightly/cu128
