Galewsky et al, 2004の浅水モデルのためのゾナルジェット初期条件のすべてのパラメータを含む構造体。デフォルト値はGalewskyに従う。

  * `latitude::Float64`: ジェットの緯度 [˚N]
  * `width::Float64`: ジェットの幅 [˚], デフォルト ≈ 19.29˚
  * `umax::Float64`: ジェットの最大速度 [m/s]
  * `perturb_lat::Float64`: 擾乱の緯度 [˚N], デフォルトではジェット内の位置
  * `perturb_lon::Float64`: 擾乱の経度 [˚E]
  * `perturb_xwidth::Float64`: 擾乱のゾナル範囲 [˚], デフォルト ≈ 19.1˚
  * `perturb_ywidth::Float64`: 擾乱の緯度範囲 [˚], デフォルト ≈ 3.8˚
  * `perturb_height::Float64`: 擾乱の振幅 [m]
