# Zebrafish Brain Image Registration

[![license](https://img.shields.io/github/license/:user/:repo.svg)](LICENSE)
[![standard-readme compliant](https://img.shields.io/badge/readme%20style-standard-brightgreen.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme)

This is a pipeline for zebra fish brain image registration.

## Description
This easy-to-use pipeline which can process fish one by one, around 30 minutes for each fish.





## Preparation

### Input
1. CSV files of ROI coordinates.
2. Atlas downloaded from [mapzebrain](https://mapzebrain.org/atlas/2d).
3. 9 Planes tiffile for each fish (or any number of planes you want ).
4. One zstack tiffile for each fish.
### Tools
1. Jupyter notebook.
2. Fuji (imageJ).
### Prerequisite
1. Motion correction.
2. Confirm the direction of atlas and your zstack being consistent.
3. Copy and save each zstack as nrrd format.

## Packages


```python
import matplotlib.pyplot as plt
import os
import numpy as np
import cv2
import tifffile
import glob
import bg_space as bg
import pandas as pd
import time
```


## Path to change
### 2D registration
In this folder, there are all your inputs of one fish, like zstack and planes.
```python
main_dir = "/media/semmelhacklab/David_Behavior_Experiment/testfish/2023-07-06_F1_lowintensity_test"
```
Change fish number here.
```python
img2 = tifffile.imread(main_dir+'/F1_zscan.tif')
```
### 3D registration
Change your atlas path here.
```python
reference_path = "/media/semmelhacklab/David_Behavior_Experiment/testfish/HSA.nrrd"
```
Also, the fish name.
```python
with open(sh_reg3d_path,'w') as f:
    s = 'reference='+reference_path+'\n'+\
        'directory_3d='+directory_3d+'\n'+\
        'moving_file=${directory_3d}/F1_zscan.nrrd\n'+\
```



## Check registration

### 2D: peaks in similarity plots. Open warped tiffiles and plane tiffiles in ImageJ and compare.
### 3D: Open warped zstack and atlas in ImageJ, merge them with different color and check if they match well.

## Apply transformation
### Check your ROI csv paths, and check the row names before transformation.
-You can use [this code](renametitle.py) for changing titles.

