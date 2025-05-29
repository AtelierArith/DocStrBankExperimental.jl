```
Line3D <: Pattern3D
```

2つの3Dエンドポイントの間に均一なランダム分布を持つ点。

# フィールド

  * `λ::Float64`: 線形分子密度（マイクロンあたりの分子数）
  * `endpoints::Vector{Tuple{Float64,Float64,Float64}}`: 3Dエンドポイント座標のベクター
  * `n::Int`: パターン内の分子の数
  * `x::Vector{Float64}`: マイクロン単位の分子のX位置
  * `y::Vector{Float64}`: マイクロン単位の分子のY位置
  * `z::Vector{Float64}`: マイクロン単位の分子のZ位置

# 例

```julia
# デフォルトパラメータでラインを作成
line = Line3D()

# カスタム3Dラインを作成
line = Line3D(; λ=5.0, endpoints=[(-1.0, 0.0, -0.5), (1.0, 0.0, 0.5)])
```
