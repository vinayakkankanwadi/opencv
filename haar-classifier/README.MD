# Training an OpenCV Haar Classifier

## Folder structure
```
--pos
----watch5050.jpg
--neg
----001.jpg ...
--bg.txt
--info
----info.lst
----001...jpg ...
--positives.vec 
--data
```

## Positive Image(s)
```
Copy positive image file into pos folder
Here we are just using one

--pos
----watch5050.jpg

https://github.com/vinayakkankanwadi/opencv/blob/master/haar-classifier/pos/watch5050.jpg
```

## Negative Images
```
Copy negative images into neg folder
https://github.com/vinayakkankanwadi/opencv/tree/master/haar-classifier/neg

--neg

```

## Create File Descriptor for Negative Images
```
python create_pos_n_neg.py
This should generate bg.txt file

--bg.txt

```

## Create Positive Samples
```
opencv_createsamples -img pos/watch5050.jpg -bg bg.txt -info info/info.lst -pngoutput info -maxxangle 0.5 -maxyangle 0.5 -maxzangle 0.5 -num 1950
This should generate info/info.lst along with images in infor folder
LOG: https://github.com/vinayakkankanwadi/opencv/blob/master/haar-classifier/log/create-positive-samples.txt

-- info
----infor.lst
----001...

```

## Create Vector File
```
opencv_createsamples -info info/info.lst -num 1950 -w 20 -h 20 -vec positives.vec
LOG: https://github.com/vinayakkankanwadi/opencv/blob/master/haar-classifier/log/create-vector-file.txt
This should generate positives.vec file

--positives.vec

```

## Training
```
opencv_traincascade -data data -vec positives.vec -bg bg.txt -numPos 1800 -numNeg 900 -numStages 10 -w 20 -h 20
LOG: https://github.com/vinayakkankanwadi/opencv/blob/master/haar-classifier/log/training.txt
This should generate cascade.xml file

--data
----cascade.xml

```

```
CREDIT:https://pythonprogramming.net/haar-cascade-object-detection-python-opencv-tutorial/
```
