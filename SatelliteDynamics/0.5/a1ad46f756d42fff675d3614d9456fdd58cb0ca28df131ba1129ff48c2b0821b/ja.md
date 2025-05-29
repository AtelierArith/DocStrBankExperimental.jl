大気抵抗によって引き起こされる摂動的な非保存加速度を計算します。これは、宇宙船の弾道特性が抗力係数によって表されると仮定します。

引数:

  * `x::AbstractArray{<:Real, 1}`: 惑星間参照フレームにおける衛星のカルテシアン状態 [m; m/s]
  * `rho::Real`: 大気密度 [kg/m^3]
  * `mass::Real`: 宇宙船の質量 [kg]
  * `area::Real`: 風に対する正面の断面積 [m^2]
  * `Cd::Real`: 抗力係数 [無次元]
  * `T::AbstractArray{<:Real, 2}`: 惑星間フレームから真の日時フレームへの回転行列

戻り値:

  * `a::AbstractArray{<:Real, 1}`: X、Y、およびZの惑星間方向における抵抗による加速度 [m/s^2]

参考文献:

1. O. Montenbruck, and E. Gill, *Satellite Orbits: Models, Methods and Applications*, 2012, p.83-86.
