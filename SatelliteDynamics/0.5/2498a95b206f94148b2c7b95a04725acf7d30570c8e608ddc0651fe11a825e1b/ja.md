太陽の位置を低精度の解析関数を用いてEME2000慣性フレームで計算します。

引数:

  * `epc::Epoch`: エポック

戻り値:

  * `r_sun::AbstractArray{<:Real, 1}`: 地球中心慣性フレームにおける太陽の位置ベクトル。

注意事項:

1. EME2000慣性フレームは、ほとんどの目的においてGCRFフレームと同等です。

参考文献:

1. O. Montenbruck, and E. Gill, *Satellite Orbits: Models, Methods and Applications*, 2012, p.70-73.
