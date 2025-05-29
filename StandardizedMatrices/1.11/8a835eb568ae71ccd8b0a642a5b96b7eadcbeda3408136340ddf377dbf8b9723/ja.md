行列を標準化されたものとして扱います。これは、元のデータを変更することなく、`z = StatsBase.zscore(x, 1)`のように行います。

`z = StandardizedMatrix(x::AbstractMatrix)` `z = StandardizedMatrix(x::AbstractMatrix, μ::AbstractVector, σ::AbstractVector)`
