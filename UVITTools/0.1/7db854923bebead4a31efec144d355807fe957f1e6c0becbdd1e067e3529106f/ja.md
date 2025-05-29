```
nuv_grating_m1_fluxed_spec(target,nuv_grating_image_file, ds9srcregfile, ds9bgdregfile[,order=-1, cross_disp_width_pixels= 40, outfile="default"])
```

AstroSat/UVIT NUV-Grating order=-1の分散画像からフラックスキャリブレーションされたスペクトルを抽出します。これは、ソースおよびバックグラウンドスペクトルの抽出、波長およびフラックスキャリブレーションのために他の関数を使用するメイン関数です。フラックスされたスペクトルを出力します。グレーティングオーダー、波長およびフラックスキャリブレーションの詳細については、[Dewangan (2021)](https://ui.adsabs.harvard.edu/abs/2021JApA...42...49D/abstract)を参照してください。 ...

# 引数

## 必須パラメータ

  * `target::String`: 観測されたUVITフィールドに存在するターゲットの名前。
  * `nuv_grating_image_file::String`: CCDLABを使用して生成されたFITS形式のNUV-Grating画像ファイルの名前。
  * `ds9srcregfile::String`: ゼロオーダー位置としてソース中心を持つds9領域ファイルの名前。
  * `ds9bgdregfile::String`: 画像のソースフリー領域の中心を持つds9領域ファイルの名前。

## オプションのパラメータ

  * `order::Int`: -1（デフォルト）、スペクトルを抽出するために使用されるグレーティングオーダー。許可されるオーダー=-1。オーダー=-2はまだキャリブレーションされていません。
  * `cross_disp_width_pixels::String`: 40（デフォルト）、クロス分散方向のピクセル幅。

-`outfile::String`: 出力ファイルの名前。outfile="default"の場合、ターゲット名/グレーティングに基づいたデフォルトのファイル名が生成されます。

## 出力

  * `(λ, f_λ, err_f_λ)`
  * ASCIIファイルに保存されたフラックスされたスペクトル。

...
