```
nuv_grating_phafile(target,nuv_grating1_image_file, ds9srcregfile, ds9bgdregfile[, cross_disp_width_pixels= 40])
```

AstroSat/UVIT NUV-Gratingの分散画像からXSPEC/Sherpa互換のソースおよびバックグラウンドPHAスペクトルファイルを抽出します。これはCCDLAB処理パイプラインから生成されたものです。

この関数は、DS9領域ファイルに提供されたゼロオーダー位置を使用してソースおよびバックグラウンドカウントスペクトルを抽出し、それらをPHAスペクトルファイルに変換します。グレーティングオーダーおよびスペクトル応答の詳細については、[Dewangan (2021)](https://ui.adsabs.harvard.edu/abs/2021JApA...42...49D/abstract)を参照してください。

...

# 引数

## 必須パラメータ

  * `target::String`: 観測されたUVITフィールドに存在するターゲットの名前。
  * `nuv_grating_image_file::String`: CCDLABを使用して生成されたFITS形式のNUV-Grating画像ファイルの名前。
  * `ds9srcregfile::String`: ゼロオーダー位置としてソース中心を持つds9領域ファイルの名前。
  * `ds9bgdregfile::String`: 画像のソースフリー領域の中心を持つds9領域ファイルの名前。

## オプションのパラメータ

  * `cross_disp_width_pixels::String`: 40（デフォルト）、クロス分散方向のピクセル幅。
  * `respdir::String`: ローカルマシンにおける応答行列を含むディレクトリの名前。応答ファイルはGitHubページからダウンロードできます。

#必要なキーワードを読み込む`

## 出力

  * ソースおよびバックグラウンドPHAファイル。
  * 一部の関連情報も画面に表示されます。

...
