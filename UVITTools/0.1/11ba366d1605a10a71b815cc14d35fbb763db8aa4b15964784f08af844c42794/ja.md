`nuv_grating_m1_net_countrate_spec(nuv_grating_image_file, ds9srcregfile, ds9bgdregfile[, cross_disp_width_pixels = 40,  outfile="nuv_grating_m1_net_countrate_spec.dat"])` 

AstroSat/UVIT NUV-Gratingの分散画像から、CCDLAB処理パイプラインを使用して生成された背景補正済みのネットカウントレートスペクトルを抽出します。

...

# 引数

## 必須パラメータ

  * `nuv_grating_image_file::String`: CCDLABを使用して生成されたFITS形式のNUV-Grating画像ファイルの名前。
  * `ds9srcregfile::String`: ゼロオーダー位置を中心とするソースのds9領域ファイルの名前。
  * `ds9bgdregfile::String`: 画像のソースフリー領域の中心を持つds9領域ファイルの名前。

## オプションパラメータ

  * `cross_disp_width_pixels::String`: 40（デフォルト）、横方向のピクセル幅。
  * `outfile::String`: ASCII出力ファイル名の名前。デフォルトファイル名: "`nuv_grating_m1_net_countrate_spec.dat`"。

...
