```
generate_perimeter_point(norm_distance_on_perimeter::Float64, Γ::Matrix{Float64}, θmle::Vector{Float64}, ind1::Int, ind2::Int; confidence_level::Float64=0.01)
```

[`generate_perimeter_point(norm_distance_on_perimeter::Float64, e::Ellipse)`](@ref)を呼び出す別の方法で、正方行列Γを提供し、最大尤度推定における対数尤度関数のヘッセ行列の逆行列、関心のある2つの変数のインデックス、および対数尤度関数の2D楕円近似を表す信頼レベルを指定します。

# 引数

  * `norm_distance_on_perimeter`: 楕円の周囲の正規化された距離を表す数 ∈ [0.0,1.0]。値0.5は楕円の周囲の中間点に対応し、値0.7は楕円の周囲の70%の位置に対応します。
  * `Γ`: 最大尤度推定における対数尤度関数のヘッセ行列の逆行列である正方行列（2D）。
  * `θmle`: パラメータの最大尤度推定。
  * `ind1`: 関心のある最初のパラメータのインデックス（`Γ`の行と列のインデックスに対応）。
  * `ind2`: 関心のある2番目のパラメータのインデックス（`Γ`の行と列のインデックスに対応）。

# キーワード引数

  * `confidence_level`: 楕円近似が構築される信頼レベル ∈ [0.0,1.0]。デフォルトは`0.01`です。
