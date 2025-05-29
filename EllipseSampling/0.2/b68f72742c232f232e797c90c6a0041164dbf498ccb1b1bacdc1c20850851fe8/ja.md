```
generate_N_clustered_points(num_points::Int, Γ::Matrix{Float64}, θmle::Vector{Float64}, ind1::Int, ind2::Int; 
    confidence_level::Float64=0.01, dof::Int=2, start_point_shift::Float64=rand(), sqrt_distortion::Float64=0.0)
```

[`generate_N_clustered_points(num_points::Int, e::Ellipse; start_point_shift::Float64=rand(), sqrt_distortion::Float64=0.)`](@ref)を呼び出す別の方法で、正方行列Γを供給し、最大尤度推定における対数尤度関数のヘッセ行列の逆行列、関心のある2つの変数のインデックス、および対数尤度関数の2D楕円近似を表す信頼レベルを指定します。

# 引数

  * `num_points`: 楕円上に等間隔で生成する点の正の整数の数。
  * `Γ`: 最大尤度推定における対数尤度関数のヘッセ行列の逆行列である正方行列（2D）。
  * `θmle`: パラメータの最大尤度推定。
  * `ind1`: 関心のある最初のパラメータのインデックス（`Γ`の行および列のインデックスに対応）。
  * `ind2`: 関心のある2番目のパラメータのインデックス（`Γ`の行および列のインデックスに対応）。

# キーワード引数

  * `confidence_level`: 楕円近似が構築される信頼レベル ∈ [0.0,1.0]。デフォルトは `0.01`。
  * `dof`: 楕円を定義する漸近的信頼閾値の計算に使用される自由度の整数。デフォルトは `2`。
  * `start_point_shift`: 数値 ∈ [0.0,1.0]。デフォルトは `rand()`（[0.0,1.0]で定義）、つまり、デフォルトではこの関数が呼び出されるたびに異なる点のセットが生成されます。
  * `sqrt_distortion`: 数値 ∈ [0.0,1.0]。デフォルトは `0.0`、つまり、デフォルトではこの関数はパラメータ `t` に関して楕円 `e` 上に点を均等に配置します。
