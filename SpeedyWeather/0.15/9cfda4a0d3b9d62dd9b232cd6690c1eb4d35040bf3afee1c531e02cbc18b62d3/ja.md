変換された予測変数（および u, v, temp_virt）をグリッドポイント空間に変換しました。

  * `nlat_half::Int64`
  * `nlayers::Int64`
  * `vor_grid::Any`: 水平風の相対渦度 [1/s]
  * `div_grid::Any`: 水平風の発散 [1/s]
  * `temp_grid::Any`: 絶対温度 [K]
  * `temp_virt_grid::Any`: 仮想温度 [K]
  * `humid_grid::Any`: 比湿 [kg/kg]
  * `u_grid::Any`: ゾナル速度 [m/s]
  * `v_grid::Any`: 経度方向の速度 [m/s]
  * `pres_grid::Any`: 表面圧力の対数 [Pa]
  * `tracers_grid::Dict{Symbol}`: トレーサー [?]
  * `random_pattern::Any`: ランダムプロセスによって制御されるランダムパターン [1]
  * `temp_grid_prev::Any`: 前の時間ステップでの絶対温度 [K]
  * `humid_grid_prev::Any`: 前の時間ステップでの比湿 [kg/kg]
  * `u_grid_prev::Any`: 前の時間ステップでのゾナル速度 [m/s]
  * `v_grid_prev::Any`: 前の時間ステップでの経度方向の速度 [m/s]
  * `pres_grid_prev::Any`: 前の時間ステップでの表面圧力の対数 [Pa]
  * `tracers_grid_prev::Dict{Symbol}`: 前の時間ステップでのトレーサー [?]
