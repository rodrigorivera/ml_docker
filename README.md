# Machine Learning and Deep Learning Docker Image

A docker image to run Anaconda and other popular libraries for machine learning

## Included Libraries

* Ubuntu 16.04
* CUDA 9.1 (GPU version only)
* cuDNN v7 (GPU version only)
* [Anaconda 4.4.0 Package (Python 3.6)](https://repo.continuum.io/archive/Anaconda3-5.2.0-Linux-x86_64.sh) [**Jupyter Notebook included**]
* [Keras](https://github.com/fchollet/keras)
* [Tensorflow](https://github.com/tensorflow/tensorflow)
* [PyTorch](http://pytorch.org/)
* [MXNet](https://mxnet.incubator.apache.org/get_started/install.html)

## To be Included

* Caffe
* OpenCV
* CNTK

#### CPU
1. Installing Docker
    * Installing Docker on Ubuntu 14.04:
    <br/>```sudo bash install_docker/docker_install1404.sh```
    * Installing Docker on Ubuntu 16.04 or above:
    <br/>```sudo bash install_docker/docker_install1604.sh```
2. Building Docker Image: 
<br/>```sudo docker build -t riverar_docker_tfgpu_conda -f dockerfile.cpu .```
3. Running the Docker Container 
<br/>```sudo docker run -it -p 8888:8888 -p 6006:6006 -v /sharedfolder:/root/sharedfolder riverar_docker_tfgpu_conda:latest bash``` 

### GPU
1. Installing Docker
    * Installing Docker on Ubuntu 14.04:
    <br/>```sudo bash install_docker/docker_install1404.sh```
    * Installing Docker on Ubuntu 16.04 or above:
    <br/>```sudo bash install_docker/docker_install1604.sh```
2. Installing NVIDIA-Docker
<br/>```sudo bash nvidia_docker.sh```
3. Building Docker Image
<br/>```sudo docker build -t riverar_docker_tfgpu_conda -f dockerfile.gpu .```
4. Restarting Nvidia-docker
<br/>```sudo systemctl restart nvidia-docker```
4. Running the Docker Container
<br/>```sudo nvidia-docker run -it -p 8888:8888 -p 6006:6006 -v /sharedfolder:/root/sharedfolder riverar_docker_tfgpu_conda:latest bash```

### Running Jupyter notebook
**```jupyter notebook --allow-root```**

*Note*: You can remove __```-v /sharedfolder:/root/sharedfolder```__ from CPU as well as GPU if you're running the container on cloud. This command is to just link your local files on the container.

### Some Handy commands
1. Removing all containers
<br/>```sudo docker rm $(sudo docker ps -a -f status=exited -q)```
2. Removing all images
<br/>```sudo docker rmi $(sudo docker images -a -q)```


##### Issues
**If there is any issue, please feel free to open an issue**


