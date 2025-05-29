```
Line2D <: Pattern2D
```

2つの端点の間に均一なランダム分布を持つ点。

# フィールド

  * `λ::Float64`: 線形分子密度（マイクロンあたりの分子数）
  * `endpoints::Vector{Tuple{Float64,Float64}}`: 端点座標のベクター
  * `n::Int`: パターン内の分子の数
  * `x::Vector{Float64}`: マイクロン単位の分子のX位置
  * `y::Vector{Float64}`: マイクロン単位の分子のY位置

# 例

```julia
# デフォルトパラメータでラインを作成
line = Line2D()

# カスタムラインを作成
line = Line2D(; λ=5.0, endpoints=[(-2.0, 0.0), (2.0, 0.0)])
```
