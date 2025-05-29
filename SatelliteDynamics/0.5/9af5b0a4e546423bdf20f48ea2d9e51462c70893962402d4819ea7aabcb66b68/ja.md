地球の重力によって引き起こされる加速度を球面調和重力場でモデル化して計算します。

引数:

  * `r_sat::AbstractArray{<:Real, 1}`: 惑星慣性系における衛星の位置 [m]
  * `R_eci_ecef::AbstractArray{<:Real, 2}`: ベクトルを慣性系から体固定参照系に変換する回転行列。
  * `n_max::Integer`: 展開に使用する最大次数係数
  * `m_max::Integer`: 展開に使用する最大次数係数。次数より小さい必要があります。

戻り値:

  * `a::AbstractArray{<:Real, 1}`: X、Y、Z慣性方向における重力加速度 [m/s^2]

参考文献:

1. O. Montenbruck, and E. Gill, *Satellite Orbits: Models, Methods and Applications*, 2012, p.56-68.
