粒子輸送の診断変数

  * `nparticles::Int64`: 粒子の数
  * `nlat_half::Int64`: 一つの半球の緯度の数（Eq. 含む）、グリッドの解像度パラメータ
  * `locations::Any`: 作業配列：粒子の位置
  * `u::Any`: 作業配列：速度 u
  * `v::Any`: 作業配列：速度 v
  * `σ_tend::Any`: 作業配列：速度 w = dσ/dt
  * `interpolator::SpeedyWeather.RingGrids.AnvilInterpolator`: 粒子の位置に速度場を補間するための補間器
