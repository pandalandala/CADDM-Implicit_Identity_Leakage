## Dependencies

* Python 3 >= 3.6
* Pytorch >= 1.6.0
* OpenCV >= 4.4.0
* Scipy >= 1.4.1
* NumPy >= 1.19.5

## Data Preparation

##### Take FF++ as an example:

1. Download the dataset from [FF++](https://github.com/ondyari/FaceForensics) and put them under the *./data*.

```
.
└── data
    └── FaceForensics++
        ├── original_sequences
        │   └── youtube
        │       └── raw
        │           └── videos
        │               └── *.mp4
        ├── manipulated_sequences
        │   ├── Deepfakes
        │       └── raw
        │           └── videos
        │               └── *.mp4
        │   ├── Face2Face
        │		...
        │   ├── FaceSwap
        │		...
        │   ├── NeuralTextures
        │		...
        │   ├── FaceShifter
        │		...
```

2. Download the landmark detector from [here](https://github.com/codeniko/shape_predictor_81_face_landmarks) and put it in the folder *./lib*.

3. Run the code to extract frames from FF++ videos and save them under the *./train_images* or *./test_images* based on the division in the original dataset.

   ```
    python lib/extract_frames_ldm_ff++.py
   ```

## Pretrained weights

You can download pretrained weights [here](https://drive.google.com/file/d/1JNMI4RGssgCOl9t05jkUa6imnw5XR5id/view?usp=sharing). 

## Evaluations

To evaluate the model performance, please run: 

```
python test.py   --cfg ./configs/caddm_test.cfg
```

## Results

Our model achieved the following performance on:

| Training Data | Backbone        | FF++       | Celeb-DF   | DFDC       |
| ------------- | --------------- | ---------- | ---------- | ---------- |
| FF++          | ResNet-34       | 99.70%     | 91.15%     | 71.49%     |
| FF++          | EfficientNet-b3 | 99.78%     | 93.08%     | 73.34%     |
| FF++          | EfficientNet-b4 | **99.79%** | **93.88%** | **73.85%** |

Note: the metric is *video-level AUC*.

## Training

To train our model from scratch, please run :

```
python  train.py --cfg ./configs/caddm_train.cfg
```
