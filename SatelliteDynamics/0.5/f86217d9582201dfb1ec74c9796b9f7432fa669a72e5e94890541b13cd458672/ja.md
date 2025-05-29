衛星に対する質点近似によって引き起こされる加速度を計算します。衛星の加速度ベクトルを返します。

引数:

  * `r_sat::AbstractArray{<:Real, 1}`: 惑星慣性系における衛星の位置 [m]
  * `GM::AbstractArray{<:Real, 1}`: 引力を持つ天体の重力定数 [m^3/s^2] デフォルト: SatelliteDynamics.GM_EARTH)

(デフォルト: SatelliteDynamics.GM_EARTH)

返り値:

  * `a::AbstractArray{<:Real, 1}`: X, Y, Zの慣性方向における加速度 [m/s^2]
