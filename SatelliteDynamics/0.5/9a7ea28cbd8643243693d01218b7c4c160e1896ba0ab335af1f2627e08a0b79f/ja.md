太陽放射圧による摂動加速度を計算します。反射面が太陽に直接向けられた平面であると仮定します。

引数:

  * `x::AbstractArray{<:Real, 1}`: 惑星慣性参照系における衛星のカルテシアン状態 [m; m/s]

戻り値:

  * `a::AbstractArray{<:Real, 1}`: 太陽放射圧による衛星の加速度 [m/s^2]

参考文献:

1. O. Montenbruck, and E. Gill, *Satellite Orbits: Models, Methods and Applications*, 2012, p.77-79.
