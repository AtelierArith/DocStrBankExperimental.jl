```
LLCUSUM(x::AbstractMatrix, k::Real; ncuts::AbstractVector = [2 for _ in eachcol(x)])
```

データのカテゴリ化に基づく分布自由なログ線形CUSUM監視統計。

# フィールド

  * `k::Float64`: CUSUM統計の許容定数。
  * `value::Float64`: 統計の初期値（デフォルト: 0.0）。
  * `Sobs::Vector{Float64}`: 観測された累積カテゴリのベクトル。
  * `Sexp::Vector{Float64}`: 期待される観測カテゴリのベクトル。
  * `qtls::Vector{Vector{Float64}}`: データのカテゴリ化に使用される分位数のベクトル。
  * `f0::Vector{Float64}`: ログ線形モデルを使用して推定されたICセル確率のベクトル。
  * `table::Matrix{Float64}`: セルの組み合わせの行列。

# 参考文献

Qiu, P. (2008). Distribution-free multivariate process control based on log-linear modeling. IIE Transactions, 40(7), 664-677. https://doi.org/10.1080/07408170701744843
