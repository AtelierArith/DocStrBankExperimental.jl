```
generate_N_clustered_points(num_points::Int, x_radius::T, y_radius::T, α::T=0.0, Cx::T=0.0, Cy::T=0.0; start_point_shift::Float64=rand(), sqrt_distortion::Float64=0.0) where T<:Float64
```

楕円上に点を生成するために楕円のパラメータを指定することによって、[`generate_N_clustered_points(num_points::Int, e::Ellipse; start_point_shift::Float64=rand(), sqrt_distortion::Float64=0.)`](@ref)を呼び出す別の方法です。

# 引数

  * `num_points`: 楕円上に生成する点の数（正の整数）で、等間隔で配置されます。
  * `x_radius`: x軸における楕円の半径（すなわち、回転`α`がゼロのとき）。
  * `y_radius`: y軸における楕円の半径（すなわち、回転`α`がゼロのとき）。
  * `α`: 楕円が回転した角度（ラジアン、0から2π）。正の値は反時計回りの回転を表します。デフォルトは`0.0`です。
  * `Cx`: 楕円の中心のx座標（x軸における楕円の平行移動）。デフォルトは`0.0`です。
  * `Cy`: 楕円の中心のy座標（y軸における楕円の平行移動）。デフォルトは`0.0`です。

# キーワード引数

  * `start_point_shift`: 数値 ∈ [0.0,1.0]。デフォルトは`rand()`（[0.0,1.0]で定義される）で、デフォルトではこの関数が呼び出されるたびに異なる点のセットが生成されます。
  * `sqrt_distortion`: 数値 ∈ [0.0,1.0]。デフォルトは`0.0`で、デフォルトではこの関数はパラメータ`t`に関して楕円`e`上に点を均等に配置します。
