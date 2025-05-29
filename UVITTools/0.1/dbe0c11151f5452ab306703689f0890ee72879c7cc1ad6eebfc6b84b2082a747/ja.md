```
fuv_grating1_fluxed_spec(target,fuv_grating1_image_file, ds9srcregfile, ds9bgdregfile[, order = -2, angle_xaxis_disp_deg=0.0, cross_disp_width_pixels = 40])
```

AstroSat/UVIT FUV-Grating1の分散画像からフラックスキャリブレーションされたスペクトルを抽出します。これは、ソースおよび背景スペクトルの抽出、波長およびフラックスキャリブレーションのために他の関数を使用するメイン関数です。フラックスされたスペクトルを出力します。グレーティングオーダー、波長およびフラックスキャリブレーションの詳細については、[Dewangan (2021)](https://ui.adsabs.harvard.edu/abs/2021JApA...42...49D/abstract)を参照してください。 ...

# 引数

## 必須パラメータ

  * `target::String`: 観測されたUVITフィールドに存在するターゲットの名前。
  * `fuv_grating1_image_file::String`: CCDLABを使用して生成されたFITS形式のFUV-Grating1画像ファイルの名前。
  * `ds9srcregfile::String`: ゼロオーダー位置としてソース中心を持つds9領域ファイルの名前。
  * `ds9bgdregfile::String`: 画像のソースフリー領域の中心を持つds9領域ファイルの名前。

## オプションパラメータ

  * `order::Int`: -2（デフォルト）、スペクトルを抽出するために使用されるグレーティングオーダー。許可されるオーダーは-1および-2です。
  * `angle_xaxis_disp_deg::Float64`: 0.0（デフォルト）、分散軸とx軸の間の角度。
  * `cross_disp_width_pixels::String`: 40（デフォルト）、クロス分散方向のピクセル幅。

## 出力

  * `(λ, f_λ, err_f_λ)`
  * ASCIIファイルに保存されたフラックスされたスペクトル。
  * スペクトル抽出に使用されたDS9ソースおよび背景領域ファイル。
  * ASCIIファイルにおけるソースおよび背景カウントスペクトルデータ。
  * ASCIIファイルにおけるネットソースカウントスペクトル。

...
