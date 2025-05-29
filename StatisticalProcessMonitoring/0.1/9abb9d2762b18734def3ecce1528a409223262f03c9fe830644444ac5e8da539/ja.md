```
MOC(x::AbstractMatrix, l::Real; ncuts::AbstractVector = [3 for _ in eachcol(x)], N = 1)
```

データのカテゴリ化に基づく多変量順序カテゴリ監視統計。

# フィールド

  * `l::Float64`: 統計の指数加重平滑定数。
  * `value::Float64`: 統計の初期値（デフォルト: 0.0）。
  * `qtls::Vector{Vector{Float64}}`: データのカテゴリ化に使用される分位数のベクトル。
  * `f0::Vector{Float64}`: ログ線形モデルを使用して推定されたICセル確率のベクトル。
  * `table::Matrix{Float64}`: セルの組み合わせの行列。
  * `inv_VCOV::Matrix{Float64}`: 実行統計に使用される逆共分散を含む行列。
  * `N::Int`: 各時点での観測数（デフォルト: 1）
  * `z_k::Vector{Float64}`: 現在の平滑化された値のベクトル。

# 参考文献

Wang, J., Li, J., & Su, Q. (2017). Multivariate Ordinal Categorical Process Control Based on Log-Linear Modeling. Journal of Quality Technology, 49(2), 108-122. https://doi.org/10.1080/00224065.2017.11917983
