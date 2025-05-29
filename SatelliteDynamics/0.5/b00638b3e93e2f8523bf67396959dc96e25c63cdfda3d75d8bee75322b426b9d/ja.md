地球軌道にある衛星の照明割合を円筒形の地球影モデルを使用して計算します。

引数:

  * `x::AbstractArray{<:Real, 1}`: 惑星慣性参照系における衛星のカルテシアン状態 [m; m/s]
  * `r_sun::AbstractArray{<:Real, 1}`: 惑星慣性系における太陽の位置。

戻り値:

  * `nu::Float64`: 照明割合 (0 <= nu <= 1)。nu = 0 は宇宙船が完全に影にあることを意味し、nu = 1 は宇宙船が太陽によって完全に照らされていることを意味します。

参考文献:

1. O. Montenbruck, and E. Gill, *Satellite Orbits: Models, Methods and Applications*, 2012, p.80-83.
