```
log_image(logger::TBLogger, name::AbstractString, imgArray::AbstractArray, format::ImageFormat; step=step(logger))
```

画像データとフォーマットを使用して画像をログに記録します

  * imgArray: 画像データ。ピクセル値の1次元、2次元、または3次元の`Array`。ピクセル値は実数[0, 1]または整数[0, 255]であることができます。
  * format: 画像のフォーマット。次のいずれかである必要があります {L, LN, NL,  CL, LC, NCL, NLC, CLN, LCN,  HW, WH, HWC, WHC, CHW, CWH,  HWN, WHN, NHW, NWH,  HWCN, WHCN, CHWN, CWHN, NHWC, NWHC, NCHW, NCWH}

      * L: 長さ
      * C: チャンネル/カラー
      * H: 高さ
      * W: 幅
      * N: 観測
