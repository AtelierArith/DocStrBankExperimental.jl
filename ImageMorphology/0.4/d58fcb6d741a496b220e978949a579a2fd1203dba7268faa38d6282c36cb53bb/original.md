```
cleared_img = clearborder(img)
cleared_img = clearborder(img, width)
cleared_img = clearborder(img, width, background)
```

Returns a copy of the original image after clearing objects connected to the border of the image. Parameters:

  * img          = Binary/Grayscale input image
  * width        = Width of the border examined (Default value is 1)
  * background   = Value to be given to pixels/elements that are cleared (Default value is 0)
