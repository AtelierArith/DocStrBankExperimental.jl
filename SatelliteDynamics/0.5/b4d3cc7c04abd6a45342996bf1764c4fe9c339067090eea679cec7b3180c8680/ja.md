衛星の慣性フレームにおける摂動加速度を、特殊相対性理論と一般相対性理論の相乗効果によって計算します。

引数:

  * `x::AbstractArray{<:Real, 1}`: 慣性参照フレームにおける衛星のカルテジアン状態 [m; m/s]

戻り値:

  * `a::AbstractArray{<:Real, 1}`: 相対性理論による衛星の加速度。 [m/s^2]

参考文献:

1. O. Montenbruck, and E. Gill, *Satellite Orbits: Models, Methods and Applications*, 2012, p.110-112.
