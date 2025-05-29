`fuv_grating2_net_countrate_spec(fuv_grating2_image_file, ds9srcregfile, ds9bgdregfile[, order = -2, disp_aligned_to_xaxis=false, angle_xaxis_disp_deg=267.479, cross_disp_width_pixels = 40])` 

AstroSat/UVIT FUV-Grating2の分散画像から背景補正されたネットカウントレートスペクトルを抽出します。これはCCDLAB処理パイプラインから生成されます。

...

# 引数

## 必須パラメータ

  * `fuv_grating2_image_file::String`: CCDLABを使用して生成されたFUV-Grating2画像ファイルのFITS形式の名前。
  * `ds9srcregfile::String`: ゼロオーダー位置としてのソース中心を持つds9領域ファイルの名前。
  * `ds9bgdregfile::String`: 画像のソースフリー領域の中心を持つds9領域ファイルの名前。

## オプションパラメータ

  * `order::Int`: -2（デフォルト）、スペクトルを抽出するために使用されるグレーティングオーダー。許可されるオーダーは-1と-2です。
  * `disp_aligned_to_xaxis`: false（デフォルト）、分散軸が検出器座標のx軸に合わせて回転している場合はtrue、分散軸が回転していない場合はfalse。
  * `angle_xaxis_disp_deg`: 267.479（デフォルト）、分散方向（ゼロからマイナスオーダーまで）とx軸との間の角度（度）。

```
	分散軸が検出器座標で回転していない場合、デフォルト値が適切であるべきです。
	分散軸がx軸に合わせて回転している場合、角度は180またはゼロ度に設定する必要があります。
```

  * `cross_disp_width_pixels::Int`: 40（デフォルト）、クロス分散方向のピクセル幅。

...
