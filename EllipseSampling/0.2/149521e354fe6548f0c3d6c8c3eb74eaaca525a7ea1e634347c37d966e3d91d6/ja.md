```
generate_N_equally_spaced_points(num_points::Int, Γ::Matrix{Float64}, θmle::Vector{Float64}, ind1::Int, ind2::Int; confidence_level::Float64=0.01, start_point_shift::Float64=rand())
```

[`generate_N_equally_spaced_points(num_points::Int, e::Ellipse; start_point_shift::Float64=rand())`](@ref)を呼び出す別の方法で、正方行列Γを提供し、最大尤度推定における対数尤度関数のヘッセ行列の逆行列、関心のある2つの変数のインデックス、および対数尤度関数の2D楕円近似を表す信頼レベルを指定します。

# 引数

  * `num_points`: 楕円上に等間隔で生成するポイントの正の整数の数。
  * `Γ`: 最大尤度推定における対数尤度関数のヘッセ行列の逆行列である正方行列（2D）。
  * `θmle`: パラメータの最大尤度推定。
  * `ind1`: 関心のある最初のパラメータのインデックス（`Γ`の行と列のインデックスに対応）。
  * `ind2`: 関心のある2番目のパラメータのインデックス（`Γ`の行と列のインデックスに対応）。

# キーワード引数

  * `confidence_level`: 楕円近似が構築される信頼レベル ∈ [0.0,1.0]。デフォルトは `0.01`。
  * `start_point_shift`: 数値 ∈ [0.0,1.0]。デフォルトは `rand()`（[0.0,1.0]で定義されている）であり、デフォルトではこの関数が呼び出されるたびに異なるポイントのセットが生成されることを意味します。
