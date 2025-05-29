衛星の慣性系における太陽の引力による加速度を計算します。

引数:

  * `x::AbstractArray{<:Real, 1}`: 慣性参照系における衛星のカルテジアン状態 [m; m/s]
  * `r_sun::AbstractArray{<:Real, 1}`: 慣性系における太陽の位置。

戻り値:

  * `a::AbstractArray{<:Real, 1}`: 慣性系における太陽の重力による加速度 [m/s^2]

参考文献:

1. O. Montenbruck, and E. Gill, *Satellite Orbits: Models, Methods and Applications*, 2012, p.69-70.
