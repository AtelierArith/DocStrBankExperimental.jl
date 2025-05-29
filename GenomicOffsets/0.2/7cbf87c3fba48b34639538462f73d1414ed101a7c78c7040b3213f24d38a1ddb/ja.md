```
fit(::Type{GradientForestGO}, Y::AbstractMatrix{T1}, X::AbstractMatrix{T2}; ntrees::Int=100) where {T1<:Real,T2<:Real}
```

データ `Y` と `X` を使用して、グラデーションフォレスト遺伝子オフセットモデル（すなわち、グラデーションフォレストをフィット）を適合させます。

# 引数

  * `Y::AbstractMatrix{T1}`: 個体の遺伝子型またはアレル頻度を持つ NxL 行列。
  * `X::AbstractMatrix{T}`: 環境データを持つ NxP 行列。
  * `ntrees`: 各フォレスト（アレルごとに1つ）が持つ木の数。

# 戻り値

  * グラデーションフォレストGOモデル。
