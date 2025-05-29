```
fuv_grating1_net_countrate_spec(fuv_grating1_image_file::String, ds9srcregfile::String, ds9bgdregfile::String; order::Int = -2, angle_xaxis_disp_deg::Float64=0.0, cross_disp_width_pixels::Int = 40)
```

`fuv_grating1_net_countrate_spec(fuv_grating1_image_file, ds9srcregfile, ds9bgdregfile[, order = -2, angle_xaxis_disp_deg=0.0, cross_disp_width_pixels = 40])` 

背景補正されたネットカウントレートスペクトルを、CCDLAB処理パイプラインから生成されたAstroSat/UVIT FUV-Grating1分散画像から抽出します。

...

# 引数

## 必須パラメータ

  * `fuv_grating1_image_file::String`: CCDLABを使用して生成されたFUV-Grating1画像ファイルのFITS形式の名前。
  * `ds9srcregfile::String`: ゼロオーダー位置としてのソース中心を持つds9領域ファイルの名前。
  * `ds9bgdregfile::String`: 画像のソースフリー領域の中心を持つds9領域ファイルの名前。

## オプションパラメータ

  * `order::Int`: -2（デフォルト）、スペクトルを抽出するために使用されるグレーティングオーダー。許可されるオーダー=-1および-2。
  * `angle_xaxis_disp_deg`: 0.0（デフォルト）、分散軸とx軸の間の角度。
  * `cross_disp_width_pixels::Int`: 40（デフォルト）、クロス分散方向のピクセル幅。

## 出力

  * 抽出に使用されたDS9領域ファイルのソースおよび背景カウントスペクトル。
  * ASCIIファイルのソースおよび背景カウントスペクトル。

...
