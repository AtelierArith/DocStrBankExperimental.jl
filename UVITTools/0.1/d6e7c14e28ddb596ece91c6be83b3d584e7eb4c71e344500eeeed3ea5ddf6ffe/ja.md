`fuv_grating2_count_spec(fuv_grating2_image_file, ds9regfile[, order = -2, disp_aligned_to_xaxis = false, angle_xaxis_disp_deg = 267.479, cross_disp_width_pixels = 40, rate = true])` 

AstroSat/UVIT FUV-Grating2の分散画像からカウントレートスペクトルを抽出します。これはCCDLAB処理パイプラインから生成されます。

...

# 引数

## 必須パラメータ

  * `fuv_grating2_image_file::String`: CCDLABを使用して生成されたFUV-Grating2画像ファイルの名前（FITS形式）。
  * `ds9regfile::String`: ゼロオーダー位置を中心とするds9領域ファイルの名前。

## オプションパラメータ

  * `order::Int`: -2（デフォルト）、スペクトルを抽出するために使用されるグレーティングオーダー。許可されるオーダーは-1と-2です。
  * `disp_aligned_to_xaxis`: false（デフォルト）、分散軸が検出器座標のx軸に合わせて回転している場合はtrue、分散軸が回転していない場合はfalse。
  * `angle_xaxis_disp_deg`: 267.479（デフォルト）、分散方向（ゼロからマイナスオーダーへの）とx軸の間の角度（度）。

```
	分散軸が検出器座標で回転していない場合、デフォルト値が適切であるべきです。
	分散軸がx軸に合わせて回転している場合、角度は180または0度に設定する必要があります。
```

  * `cross_disp_width_pixels::Int`: 40（デフォルト）、クロス分散方向のピクセル幅。
  * `rate::Bool`: カウントレートスペクトルの場合はtrue（デフォルト）、そうでない場合はカウントスペクトルのためにfalse。

## 出力

  * カウントスペクトルファイル
  * 抽出領域を検証するために使用できるds9と互換性のある領域ファイル。
  * カウントスペクトル（ゼロオーダーに対するピクセル数、カウント/sまたはカウント、誤差）
