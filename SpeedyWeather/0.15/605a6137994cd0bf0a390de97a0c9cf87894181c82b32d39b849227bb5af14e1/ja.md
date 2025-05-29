スペクトルおよびグリッドポイント空間における予測変数の傾向

  * `trunc::Int64`
  * `nlat_half::Int64`
  * `nlayers::Int64`
  * `vor_tend::Any`: 水平風場の渦度 [1/s]
  * `div_tend::Any`: 水平風場の発散 [1/s]
  * `temp_tend::Any`: 絶対温度 [K]
  * `humid_tend::Any`: 比湿 [kg/kg]
  * `u_tend::Any`: 経度方向の速度 [m/s]
  * `v_tend::Any`: 緯度方向の速度 [m/s]
  * `pres_tend::Any`: 表面圧の対数 [Pa]
  * `tracers_tend::Dict{Symbol}`: トレーサー [?]
  * `u_tend_grid::Any`: 経度方向の速度 [m/s], グリッド
  * `v_tend_grid::Any`: 緯度方向の速度 [m/s], グリッド
  * `temp_tend_grid::Any`: 絶対温度 [K], グリッド
  * `humid_tend_grid::Any`: 比湿 [kg/kg], グリッド
  * `pres_tend_grid::Any`: 表面圧の対数 [Pa], グリッド
  * `tracers_tend_grid::Dict{Symbol}`: トレーサー [?], グリッド
