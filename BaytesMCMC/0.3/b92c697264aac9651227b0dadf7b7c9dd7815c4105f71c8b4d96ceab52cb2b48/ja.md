```julia
struct DualAverageParameter{T<:AbstractFloat}
```

デフォルトのデュアル平均アルゴリズムに関する情報を含みます。

# フィールド

  * `δ::AbstractFloat`: 目標受け入れ率
  * `γ::AbstractFloat`: 正則化スケール
  * `κ::AbstractFloat`: リラクゼーション指数 - 平均対数ステップサイズ用
  * `t₀::Int64`: オフセット
