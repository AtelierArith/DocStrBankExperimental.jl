```
log_images(logger::TBLogger, name::AbstractString, imgArrays::AbstractArray, format::ImageFormat; step=step(logger))
```

複数の画像を `Array` の画像とフォーマットを使用してログに記録します

  * imgArrays: 画像の `Array`、例: Array{Array{Float64, 3}, 1}. 画像の `Array` は多次元である可能性があります。
  * format: 画像の `Array` の各画像に適用されるフォーマット。{L, LN, NL,  CL, LC, NCL, NLC, CLN, LCN,  HW, WH, HWC, WHC, CHW, CWH,  HWN, WHN, NHW, NWH,  HWCN, WHCN, CHWN, CWHN, NHWC, NWHC, NCHW, NCWH} のいずれかです。
