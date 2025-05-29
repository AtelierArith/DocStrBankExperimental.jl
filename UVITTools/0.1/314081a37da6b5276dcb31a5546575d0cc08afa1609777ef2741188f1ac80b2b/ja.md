`nuv_grating_m1_count_spec(nuv_grating_image_file, ds9regfile[, cross_disp_width_pixels = 40, rate = true, outfile="nuv_grating_m1_count_spec.dat"])` 

AstroSat/UVIT NUV-Gratingの分散画像からカウントレートスペクトルを抽出します。これはCCDLAB処理パイプラインから生成されます。

...

# 引数

## 必須パラメータ

  * `nuv_grating_image_file::String`: CCDLABを使用して生成されたFITS形式のNUV-Grating画像ファイルの名前。
  * `ds9regfile::String`: ゼロオーダー位置を中心とするds9領域ファイルの名前。

## オプションパラメータ

  * `order::Int`: -2（デフォルト）、スペクトルを抽出するために使用されるグレーティングオーダー。許可されるオーダー=-1および-2。
  * `cross_disp_width_pixels::String`: 40（デフォルト）、クロス分散方向のピクセル幅。
  * `rate::Bool`: カウントレートスペクトルの場合はtrue（デフォルト）、カウントスペクトルの場合はfalse。
  * `outfile::String`: ASCII出力ファイル名の名前。デフォルトファイル名: "`nuv_grating_m1_count_spec.dat`"。

...
