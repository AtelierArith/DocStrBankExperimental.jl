衛星の慣性系における月の重力引力による加速度を計算します。

引数:

  * `x::AbstractArray{<:Real, 1}`: 慣性参照系における衛星のカルテジアン状態 [m; m/s]
  * `r_moon::AbstractArray{<:Real, 1}`: 慣性系における月の位置。

戻り値:

  * `a::AbstractArray{<:Real, 1}`: 慣性系における月の重力による加速度 [m/s^2]

参考文献:

1. O. Montenbruck, and E. Gill, *Satellite Orbits: Models, Methods and Applications*, 2012, p.69-70.
