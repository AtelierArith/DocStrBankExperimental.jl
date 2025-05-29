```
AbstractTransform
```

Abstract type of ImageNet Preprocessing pipelines. Expected interface:

  * `transform(method, image_path)`: load image and convert it to a WHC array
  * `inverse_transform(method, array)`: convert WHC[N] array to image[s]
