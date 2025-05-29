```
genomic_offset(model::RONA, X::AbstractMatrix{T}, Xpred::AbstractMatrix{T}) where T<:Real
```

RONAモデルのゲノムオフセットを計算します。

# 引数

  * `model::RONA`: RONAモデル。
  * `X::AbstractMatrix{T}`: 環境データを含むNxP行列。
  * `Xpred::Matrix{T}`: 予測された/変更された環境行列を含むNxP行列。

# 戻り値

  * RONAゲノムオフセット値の長さNのVector{Float64}。
