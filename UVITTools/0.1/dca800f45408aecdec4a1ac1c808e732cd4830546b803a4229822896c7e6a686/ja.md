```
fuv_grating2_fluxed_spec(target,fuv_grating2_image_file, ds9srcregfile, ds9bgdregfile[,order = -2, disp_aligned_to_xaxis=false, angle_xaxis_disp_deg=267.479, cross_disp_width_pixels= 40])
```

AstroSat/UVIT FUV-Grating2の分散画像からフラックスキャリブレーションされたスペクトルを抽出します。これは、ソースおよび背景スペクトルの抽出、波長およびフラックスキャリブレーションのための他の関数を使用するメイン関数です。フラックスされたスペクトルを出力します。グレーティングオーダー、波長およびフラックスキャリブレーションの詳細については、[Dewangan (2021)](https://ui.adsabs.harvard.edu/abs/2021JApA...42...49D/abstract)を参照してください。 ...

# 引数

## 必須パラメータ

  * `target::String`: 観測されたUVITフィールドに存在するターゲットの名前。
  * `fuv_grating2_image_file::String`: CCDLABを使用して生成されたFITS形式のFUV-Grating2画像ファイルの名前。
  * `ds9srcregfile::String`: ゼロオーダー位置としてソース中心を持つds9領域ファイルの名前。
  * `ds9bgdregfile::String`: 画像のソースフリー領域の中心を持つds9領域ファイルの名前。

## オプションパラメータ

  * `order::Int`: -2（デフォルト）、スペクトルを抽出するために使用されるグレーティングオーダー。許可されるオーダー=-1および-2。
  * `disp_aligned_to_xaxis`: false（デフォルト）、分散軸が検出器座標のx軸に合わせて回転している場合はtrue、分散軸が回転していない場合はfalse。
  * `angle_xaxis_disp_deg`: 267.479（デフォルト）、分散方向（ゼロからマイナスオーダーまで）とx軸の間の角度（度）。

```
	分散軸が検出器座標で回転していない場合、デフォルト値は適切であるべきです。
	分散軸がx軸に合わせて回転している場合、角度は180またはゼロ度に設定する必要があります。
```

  * `cross_disp_width_pixels::String`: 40（デフォルト）、クロス分散方向のピクセル幅。

## 出力

  * `(λ, f_λ, err_f_λ)`
  * フラックスされたスペクトルがasciiファイルに保存されます。

...
