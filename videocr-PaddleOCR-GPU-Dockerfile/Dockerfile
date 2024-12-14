FROM nvidia/cuda:11.2.2-runtime-ubuntu20.04
  RUN apt-get -y update 
  ENV DEBIAN_FRONTEND=noninteractive  
  RUN apt install -y wget python3-pip git ffmpeg openvpn
  RUN apt install -y libsm6 libxext6 
  RUN apt-get -y install cudnn9-cuda-11
  RUN apt --fix-broken install
  ENV DEBIAN_FRONTEND=noninteractive
  RUN pip install paddlepaddle-gpu==2.5.1 
  RUN pip install git+https://github.com/oliverfei/videocr-PaddleOCR.git
  RUN wget https://github.com/devmaxxing/videocr-PaddleOCR/raw/refs/heads/master/example.py
  RUN wget https://github.com/devmaxxing/videocr-PaddleOCR/raw/refs/heads/master/example_cropped.mp4
  ENV LD_LIBRARY_PATH=/usr/local/cuda-11.2/lib64:$LD_LIBRARY_PATH
  ENV CUDA_HOME=/usr/local/cuda-11.2
  RUN python3 example.py
  RUN rm -fr example.py example_cropped.mp4 example.srt
  RUN ln -s /usr/local/cuda-11.2/targets/x86_64-linux/lib/libcublas.so.11 /usr/lib/libcublas.so