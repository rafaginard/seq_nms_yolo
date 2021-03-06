# Seq_nms_YOLO

#### Membres: Yunyun SUN, Yutong YAN, Sixiang XU, Heng ZHANG

---

## Introduction
This was run in Ubuntu 18.04.4 LTS has been tested with CUDA v10.1 if you need any other version you must modify the Makefile and recompile.
![](img/index.jpg) 

This project combines **YOLOv2**([reference](https://arxiv.org/abs/1506.02640)) and **seq-nms**([reference](https://arxiv.org/abs/1602.08465)) to realise **real time video detection**.

## Steps
1. Clone the repository ```git clone https://github.com/rafaginard/seq_nms_yolo.git```;
1. Go to the directory ```cd seq_nms_yolo```;
1. Create a Conda Enviroment with python 2.7 version and use the requirements.txt from the repository. ```conda create --name TestEnv python=2.7 --file packageslist.txt```
1. Activate enviroment ```source activate TestEnv```;
1. Modify the Makefile acording to you environment. By default settings:
   * GPU=1		   # 0 if your pc doesn't support CUDA
   * CUDNN=0		# 1 if your pc does support CUDNN
   * OPENCV=0	   # 2 if your pc does support OPENCV
1. `make` the project;
1. Download yolo.weights and tiny-yolo.weights by running `wget https://pjreddie.com/media/files/yolo.weights` and `wget https://pjreddie.com/media/files/yolov2-tiny.weights`;
1. Export the paths:
    * `export PATH=/usr/local/cuda-10.1/bin${PATH:+:${PATH}}`
    * `export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-10.1/lib64`
    * `export LIBRARY_PATH=$LIBRARY_PATH:/usr/local/cuda-10.1/lib64`
1. Copy a video file to the video folder, for example, `input.mp4`;
1. In the video folder, run `python video2img.py -i input.mp4` and then `python get_pkllist.py`;
1. Return to root floder and run `python yolo_seqnms.py` to generate output images in `video/output`;
1. If you want to reconstruct a video from these output images, you can go to the video folder and run `python img2video.py -i output`

And you will see detection results in `video/output`

## Reference

This project copies lots of code from [darknet](https://github.com/pjreddie/darknet) , [Seq-NMS](https://github.com/lrghust/Seq-NMS) and  [models](https://github.com/tensorflow/models).
