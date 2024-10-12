
### Install

0. 克隆项目
   ```
   git clone https://github.com/yyxssm/E2ERobitics_Annotation
   ```
1. 安装必要的包
方法一：直接安装
     ```
     conda create -n labeling python=3.8 -y
     conda activate labeling
     pip install -r requirement.txt
     ```

方法二：基于虚拟环境yml文件安装
     ```
     conda env create -f environment.yml -n labeling
     ```
2. 下载模型

     download pretrained model file [deep_annotation_inference.h5](https://github.com/naurril/SUSTechPOINTS/releases/download/0.1/deep_annotation_inference.h5), put it into `./algos/models`
     ```
     wget https://github.com/naurril/SUSTechPOINTS/releases/download/0.1/deep_annotation_inference.h5  -P algos/models
     ```

### 启动
在终端中运行以下命令，然后访问 http://127.0.0.1:8081
```
python main.py
```


## 数据格式

````
   +- data
       +- scene1
          +- lidar
               +- 0000.pcd
               +- 0001.pcd
          +- camera
               +- front
                    +- 0000.jpg
                    +- 0001.jpg
               +- left
                    +- ...
          +- aux_lidar
               +- front
                    +- 0000.pcd
                    +- 0001.pcd
          +- radar
               +- front_points
                    +- 0000.pcd
                    +- 0001.pcd
               +- front_tracks
                    +- ...
          +- calib
               +- camera
                    +- front.json
                    +- left.json
               +- radar
                    +- front_points.json
                    +- front_tracks.json
          +- label
               +- 0000.json
               +- 0001.json
       +- scene2

````

标签文件夹是用于保存标注结果的目录。

calib 是从点云到图像的校准矩阵。它是可选的，但如果提供了该矩阵，框将投影到图像上以辅助标注工作。

可以查看 `./data/example` 目录下的示例。