```
cutoff!(X::AbstractVecOrMat{T}, α::T, weighted::Bool=false) where {T<:AbstractFloat}
```

SimSpreadの類似性カットオフ関数に基づいて、ベクトルまたは行列`X`をインプレースで変換します。

# 引数

  * `X::AbstractVecOrMat{AbstractFloat}` : 変換する行列またはベクトル
  * `α::AbstractFloat` : 類似性の閾値
  * `weighted::Bool` : 結果に重み付け関数を適用するかどうか（デフォルト = false）
