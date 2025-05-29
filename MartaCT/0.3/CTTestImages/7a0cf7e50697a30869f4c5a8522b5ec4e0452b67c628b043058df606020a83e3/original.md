```
ImageParams([T=Float32]; <keyword arguments>) where {T}
```

Construct ImageParams object.

# Arguments:

  * `width=200`: width of the rectangle gray scale image.
  * `height=40`: height of the rectangle gray scale image.
  * `pad=30`: padding around image.
  * `dist=10`: distance between images.
  * `radius=20`: radius of calibration circle.
  * `gray_scale=1000..1000`: interval of gray scale values.
  * `calibration_value=nothing`: value of the calibration circle. If not specified, is `gray_scale[2]`.
  * `background=nothing`: value to be used as background.
  * `hounsfield=false`: whether the gray scale should be in Hounsfield units.
