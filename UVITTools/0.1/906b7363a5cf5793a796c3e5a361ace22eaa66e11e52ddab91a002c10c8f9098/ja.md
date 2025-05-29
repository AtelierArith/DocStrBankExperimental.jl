`fuv_grating1_wavelength_calib(pixels, netsrc_spec_counts_per_s[, order = -2])`

ゼロオーダーに対するピクセル番号を波長に変換します。

この関数は、FUV-Grating1カウントスペクトルの波長キャリブレーションに使用されます。

...

# 引数

## 必須パラメータ

  * `pixels::Array`: ゼロオーダーに対するピクセル番号の配列。
  * `netsrc_spec_counts_per_s::Array`: 相対ピクセル番号に対応するネットカウントレートの配列。

## オプションパラメータ

  * `order::Int`: -2（デフォルト）、グレーティングオーダー。許可されるオーダーは-1と-2です。

...
