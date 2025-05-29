```
fit(::Type{M}, X::Union{AbstractMatrix{T},SparseMatrixCSC{T}},
    y::AbstractVector{T}; quantile::AbstractFloat=0.5,
    dofit::Bool          = true,
    wts::FPVector        = similar(y, 0),
    fitdispersion::Bool  = false,
    fitargs...) where {M<:QuantileRegression, T<:AbstractFloat}
```

モデル行列（または式）Xと応答ベクトル（またはデータフレーム）yを用いて、分位点回帰モデルをフィットします。

これは、正確な内部法を使用して解決されます。

# 引数

  * `X`: モデル行列（密行列または疎行列のいずれか）または式
  * `y`: 応答ベクトルまたはデータフレーム。

# キーワード

  * `quantile::AbstractFloat=0.5`: 回帰のための分位点値、0と1の間。
  * `dofit::Bool = true`: `false`の場合、フィッティングせずにモデルオブジェクトを返す;
  * `wts::Vector = []`: 重みベクトル、重みが使用されない場合は空であるべき;
  * `fitdispersion::Bool = false`: 分散を再評価する;
  * `fitargs...`: イテレーションの詳細を印刷するための`verbose`のような他のキーワード引数。

# 出力

RobustLinearModelオブジェクト。
