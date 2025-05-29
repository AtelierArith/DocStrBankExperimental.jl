```
log_images(logger::TBLogger, name::AbstractString, imgArrays::AbstractArray, format::ImageFormat; step=step(logger))
```

Log multiple images using `Array` of images and format

  * imgArrays: `Array` of images, e.g. Array{Array{Float64, 3}, 1}. `Array` of images can be multidimensional.
  * format: format which applies to each image in the `Array` of images. It can be one of {L, LN, NL,  CL, LC, NCL, NLC, CLN, LCN,  HW, WH, HWC, WHC, CHW, CWH,  HWN, WHN, NHW, NWH,  HWCN, WHCN, CHWN, CWHN, NHWC, NWHC, NCHW, NCWH}
