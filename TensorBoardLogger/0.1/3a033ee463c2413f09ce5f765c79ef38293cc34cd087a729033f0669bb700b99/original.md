```
log_image(logger::TBLogger, name::AbstractString, imgArray::AbstractArray, format::ImageFormat; step=step(logger))
```

Log an image using image data and format

  * imgArray: image data. A 1-D, 2-D or 3-D `Array` of pixel values. pixel values can be Real [0, 1] or Integer[0, 255]
  * format: format of the image. It can be one of {L, LN, NL,  CL, LC, NCL, NLC, CLN, LCN,  HW, WH, HWC, WHC, CHW, CWH,  HWN, WHN, NHW, NWH,  HWCN, WHCN, CHWN, CWHN, NHWC, NWHC, NCHW, NCWH}

      * L: Length
      * C: Channel/Color
      * H: Height
      * W: Width
      * N: Observation
