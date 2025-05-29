```
fuv_grating1_phafile(target,fuv_grating1_image_file, ds9srcregfile, ds9bgdregfile[,order = -2, angle_xaxis_disp_deg=0.0, cross_disp_width_pixels= 40])
```

AstroSat/UVIT FUV-Grating1分散画像からXSPEC/Sherpa互換のソースおよび背景PHAスペクトルファイルを抽出します。これはCCDLAB処理パイプラインから生成されたものです。

この関数は、DS9領域ファイルに提供されたゼロオーダー位置を使用してソースおよび背景カウントスペクトルを抽出し、それらをPHAスペクトルファイルに変換します。グレーティングオーダーおよびスペクトル応答の詳細については、[Dewangan (2021)](https://ui.adsabs.harvard.edu/abs/2021JApA...42...49D/abstract)を参照してください。

...

# 引数

## 必須パラメータ

  * `target::String`: 観測されたUVITフィールドに存在するターゲットの名前。
  * `fuv_grating1_image_file::String`: CCDLABを使用して生成されたFUV-Grating1画像ファイルの名前（FITS形式）。
  * `ds9srcregfile::String`: ゼロオーダー位置としてソース中心を持つds9領域ファイルの名前。
  * `ds9bgdregfile::String`: 画像のソースフリー領域の中心を持つds9領域ファイルの名前。

## オプションのパラメータ

  * `order::Int`: -2（デフォルト）、スペクトルを抽出するために使用されるグレーティングオーダー。許可されるオーダー=-1および-2。
  * `angle_xaxis_disp_deg::Float64`: 0.0（デフォルト）、分散軸とx軸の間の角度。
  * `cross_disp_width_pixels::Int`: 40（デフォルト）、クロス分散方向のピクセル幅。

#必要なキーワードを読み込む`

## 出力

  * ソーススペクトルファイルで更新されたRESPFILEキーを持つソースおよび背景PHAファイル
  * カウントスペクトルを抽出するために使用されたソースおよび背景DS9領域ファイル
  * ASCIIファイル内のソースおよび背景カウントスペクトル
  * ASCIIファイル内のネットソースカウントスペクトル
  * 一部の関連情報も画面に表示されます。

...
