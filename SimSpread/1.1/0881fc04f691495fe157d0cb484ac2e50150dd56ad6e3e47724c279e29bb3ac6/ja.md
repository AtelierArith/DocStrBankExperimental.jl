```
cutoff(x::T, α::T, weighted::Bool=false) where {T<:AbstractFloat}
```

SimSpreadの類似性カットオフ関数に基づいて`x`を変換します。

# 引数

  * `x::AbstractFloat` : 変換する値
  * `α::AbstractFloat` : 類似性カットオフ
  * `weighted::Bool` : 結果に重み付け関数を適用するかどうか（デフォルト = false）
