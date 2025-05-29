AstroSat/UVITペイロードからのデータをCCDLABで処理したツールのリスト。

## UVITフォトメトリー

  * `read_ds9reg` : DS9領域ファイルを読み込む。
  * `uvit_aphot` : UVIT画像に対して任意の広帯域フィルターでアパーチャフォトメトリーを実行する。
  * `uvit_countrate2flux`: 任意のフィルターに対してカウントレートをフラックス密度に変換する。
  * `uvit_filter2pha`: UVIT画像からXSPECと互換性のあるソースおよびPHAスペクトルファイルを生成する。
  * `uvit_saturation_corr` : 飽和補正を実行する。
  * `uvit_zp_uc`: Tandon et al. 2020を使用して、ゼロポイントと単位変換係数を印刷する。

## グレーティング分光法

  * `xycen_from_ds9reg`: DS9円形領域ファイルのx,y中心を読み込む。
  * `write_uvit_grating_phafile`: UVITグレーティング用のPHAスペクトルファイルを書き込む。
  * `fuv_grating1_count_spec`: FUV-Grating1画像ファイルから1次元カウントスペクトルを抽出する。
  * `fuv_grating1_net_countrate_spec`: FUV-Grating1画像から背景補正されたネットカウントレートスペクトルを導出する。
  * `fuv_grating1_pixel2lamA` : FUV-Grating1のピクセル番号をゼロオーダー位置に対して波長（Å）に変換する。
  * `fuv_grating1_wavelength_calib`: FUV-Grating1カウントスペクトルの波長キャリブレーションを実行する。
  * `fuv_grating1_flux_calib`: FUV-Grating1波長キャリブレーションされたカウントスペクトルのフラックスキャリブレーションを実行する。
  * `fuv_grating1_fluxed_spec`: FUV-Grating1画像から波長およびフラックスキャリブレーションされたスペクトルを生成する。
  * `fuv_grating1_phafile`: FUV-Grating1画像からPHAスペクトルファイルを生成する。
  * `fuv_grating1_ea` : FUV-Grating1の有効面積を印刷する。
  * `fuv_grating2_count_spec` : FUV-Grating2画像ファイルから1次元カウントスペクトルを抽出する。
  * `fuv_grating2_net_countrate_spec`: FUV-Grating2画像から背景補正されたネットカウントレートスペクトルを導出する。
  * `fuv_grating2_pixel2lamA`:  FUV-Grating2のピクセル番号をゼロオーダー位置に対して波長（Å）に変換する。
  * `fuv_grating2_wavelength_calib`: FUV-Grating2カウントスペクトルの波長キャリブレーションを実行する。
  * `fuv_grating2_flux_calib`: FUV-Grating2波長キャリブレーションされたカウントスペクトルのフラックスキャリブレーションを実行する。
  * `fuv_grating2_fluxed_spec`: FUV-Grating2画像から波長およびフラックスキャリブレーションされたスペクトルを生成する。
  * `fuv_grating2_phafile`: FUV-Grating2画像からPHAスペクトルファイルを生成する。
  * `fuv_grating2_ea`: FUV-Grating1の有効面積を印刷する。
  * `nuv_grating_m1_count_spec`: NUV-Grating画像ファイルから1次元カウントスペクトルを抽出する。
  * `nuv_grating_m1_net_countrate_spec`: NUV-Grating画像から背景補正されたネットカウントレートスペクトルを導出する。
  * `nuv_grating_m1_wavelength_calib`: NUV-Gratingカウントスペクトルの波長キャリブレーションを実行する。
  * `nuv_grating_m1_flux_calib`: NUV-Grating波長キャリブレーションされたカウントスペクトルのフラックスキャリブレーションを実行する。
  * `nuv_grating_m1_fluxed_spec`: NUV-Grating画像から波長およびフラックスキャリブレーションされたスペクトルを生成する。
  * `nuv_grating_phafile`: NUV-Grating画像からPHAスペクトルファイルを生成する。

## 単位変換

  * `lambdaA2keV` : Å単位の波長をkeV単位のエネルギーに変換する。
  * `lambdaA2ergs` : Å単位のλをエルグ単位のエネルギーに変換する。
  * `flux_density_photons2cgs` : 光子フラックス密度n*λ（光子/cm2/s/Å）をエネルギーフラックス密度f*λ（エルグ/cm2/s/Å）に変換する。
  * `flux_density_cgs2photons` : フラックス密度f*λ（エルグ/cm2/s/Å）を光子数密度n*λ（光子/cm2/s/Å）に変換する。

任意のツール（例：`nuv_grating_phafile`）の詳細なヘルプを表示するには、次のように入力します。

```julia
julia>?
help?> nuv_grating_phafile
```
