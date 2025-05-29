```
genomic_offset(model::GradientForestGO, X::AbstractMatrix{T}, Xpred::AbstractMatrix{T}) where T<:Real
```

グラデーションフォレストのゲノムオフセットを計算します。注意！私たちの実装は外挿を行わないため、試みると予測不可能な結果が得られる可能性があります。

# 引数

  * `model::GradientForestGO`: ジオメトリックGOモデル。
  * `X::AbstractMatrix{T}`: 環境データを含むNxP行列。モデルが中心とスケールをtrueに設定してフィッティングされた場合、データはスケーリングおよびセンタリングされます。
  * `Xpred::Matrix{T}`: 予測された/変更された環境行列を含むNxP行列。モデルが中心とスケールをtrueに設定してフィッティングされた場合、データはスケーリングおよびセンタリングされます。

# 戻り値

  * グラデーションフォレストのゲノムオフセット値を持つ長さNのVector{Float64}。
