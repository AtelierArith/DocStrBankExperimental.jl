```
cutoff(M::AbstractVecOrMat{T}, α::T, weighted::Bool=false) where {T<:AbstractFloat}
```

SimSpreadの類似性カットオフ関数に基づいてベクトルまたは行列`X`を変換します。

# 引数

  * `X::AbstractVecOrMat{AbstractFloat}` : 変換する行列またはベクトル
  * `α::AbstractFloat` : 類似性カットオフ
  * `weighted::Bool` : 結果に重み付け関数を適用するかどうか（デフォルト = false）
