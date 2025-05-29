```
genomic_offset(model::RDAGO, X::AbstractMatrix{T}, Xpred::AbstractMatrix{T}) where T<:Real
```

RDAゲノムオフセットを計算します。

# 引数

  * `model::RDAGO`: RDAGOモデル。
  * `X::AbstractMatrix{T}`: 環境データを含むNxP行列。
  * `Xpred::Matrix{T}`: 予測された/変更された環境行列を含むNxP行列。
  * `weighted::Bool=false`: 真の場合、投影空間におけるユークリッド距離は各軸の固有値に基づいて重み付けされます。

# 戻り値

  * RDAGOゲノムオフセット値を持つ長さNのVector{Float64}。
