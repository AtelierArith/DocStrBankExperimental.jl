与えられた層の動力学のための中間量。

  * `trunc::Int64`
  * `nlat_half::Int64`
  * `nlayers::Int64`
  * `a::Any`: 多目的のa、さまざまな場所で再利用される3D作業配列
  * `b::Any`: 多目的のb、さまざまな場所で再利用される3D作業配列
  * `a_grid::Any`: 多目的のa、さまざまな場所で再利用される3D作業配列
  * `b_grid::Any`: 多目的のb、さまざまな場所で再利用される3D作業配列
  * `a_2D::Any`: 多目的のa、さまざまな場所で再利用される作業配列
  * `b_2D::Any`: 多目的のb、さまざまな場所で再利用される作業配列
  * `a_2D_grid::Any`: 多目的のa、さまざまな場所で再利用される作業配列
  * `b_2D_grid::Any`: 多目的のb、さまざまな場所で再利用される作業配列
  * `uv∇lnp::Any`: 圧力フラックス (uₖ, vₖ)⋅∇ln(pₛ)
  * `uv∇lnp_sum_above::Any`: 上部のΔσₖ加重uv∇lnpの合計
  * `div_sum_above::Any`: 上からkまでのdiv_weightedの合計
  * `temp_virt::Any`: 仮想温度 [K]、重力ポテンシャルのためのスペクトル
  * `geopot::Any`: 完全層の重力ポテンシャル [m²/s²]
  * `σ_tend::Any`: 垂直速度 (dσ/dt)、下の半レベルk+1/2で、表面に向かっている (σ=1)
  * `∇lnp_x::Any`: 表面圧の対数の経度勾配
  * `∇lnp_y::Any`: 表面圧の対数の緯度勾配
  * `u_mean_grid::Any`: 経度速度の垂直平均 [m/s]
  * `v_mean_grid::Any`: 緯度速度の垂直平均 [m/s]
  * `div_mean_grid::Any`: 発散の垂直平均 [1/s]、グリッド
  * `div_mean::Any`: 発散の垂直平均 [1/s]、スペクトル
