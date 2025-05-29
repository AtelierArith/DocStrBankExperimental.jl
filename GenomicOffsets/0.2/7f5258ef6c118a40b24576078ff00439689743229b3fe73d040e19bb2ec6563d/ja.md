```
genomic_offset(model::GeometricGO, X::AbstractMatrix{T}, Xpred::AbstractMatrix{T}) where T<:Real
```

ジオメトリックゲノムオフセットを計算します。

# 引数

  * `model::GeometricGO`: GeometricGOモデル。
  * `X::AbstractMatrix{T}`: 環境データを含むNxP行列。モデルがcenterとscaleをtrueに設定してフィッティングされた場合、データはスケーリングおよびセンタリングされます。
  * `Xpred::Matrix{T}`: 予測された/変更された環境行列を含むNxP行列。モデルがcenterとscaleをtrueに設定してフィッティングされた場合、データはスケーリングおよびセンタリングされます。

# 戻り値

  * ジオメトリックゲノムオフセット値を持つ長さNのVector{Float64}。
