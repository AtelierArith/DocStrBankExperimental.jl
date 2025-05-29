`fuv_grating2_wavelength_calib(pixels, netsrc_spec_counts_per_s[, order = -2])`

ゼロに対する相対的なピクセル番号を波長に変換します。

この関数は、FUV-Grating2カウントスペクトルの波長キャリブレーションに使用されます。

...

# 引数

## 必須パラメータ

  * `pixels::Array`: ゼロオーダーに対する相対的なピクセル番号の配列。
  * `netsrc_spec_counts_per_s::Array`: 相対ピクセル番号に対応するネットカウント率の配列。

## オプションのパラメータ

  * `order::Int`: -2（デフォルト）、グレーティングオーダー。許可されるオーダー=-1および-2。

...
