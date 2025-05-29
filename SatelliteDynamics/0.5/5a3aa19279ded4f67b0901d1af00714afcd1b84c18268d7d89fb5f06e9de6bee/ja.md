衛星の加速度を、中心体の点質量近似によって計算します。衛星の加速度ベクトルを返します。

衛星は中心体よりもはるかに質量が小さいと仮定します。

引数:

  * `r_sat::AbstractArray{<:Real, 1}`: 共通慣性系における衛星の位置 [m]
  * `r_body::AbstractArray{<:Real, 1}`: 共通慣性系における体の位置 [m]
  * `GM::AbstractArray{<:Real, 1}`: 引力を持つ体の重力定数 [m^3/s^2] デフォルト: SatelliteDynamics.GM_EARTH)

(デフォルト: SatelliteDynamics.GM_EARTH)

戻り値:

  * `a::AbstractArray{<:Real, 1}`: X、Y、および Z の慣性方向における加速度 [m/s^2]
