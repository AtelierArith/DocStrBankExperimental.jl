ハリス-プリースター密度モデルを使用して局所密度を計算します。

引数:

  * `x::AbstractArray{<:Real, 1}`: 惑星慣性参照系における衛星のカルテシアン状態 [m; m/s]
  * `r_sun::AbstractArray{<:Real, 1}`: 惑星慣性系における太陽の位置。

戻り値:

  * `rho:Float64`: 局所大気密度 [kg/m^3]

参考文献:

1. O. Montenbruck, and E. Gill, *Satellite Orbits: Models, Methods and Applications*, 2012, p.89-91.
