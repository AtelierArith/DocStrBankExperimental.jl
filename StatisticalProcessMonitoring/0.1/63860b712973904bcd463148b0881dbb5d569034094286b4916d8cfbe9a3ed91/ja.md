```
LLD(x::AbstractMatrix, l::Real; ncuts::AbstractVector = [3 for _ in eachcol(x)], N = 1)
```

データのカテゴリ化に基づく対数線形方向モニタリング統計量。

# フィールド

  * `l::Float64`: 統計量の指数加重平滑定数。
  * `value::Float64`: 統計量の初期値（デフォルト: 0.0）。
  * `qtls::Vector{Vector{Float64}}`: データのカテゴリ化に使用される分位数のベクトル。
  * `f0::Vector{Float64}`: ログ線形モデルを使用して推定されたICセル確率のベクトル。
  * `table::Matrix{Float64}`: セルの組み合わせの行列。
  * `Sigma::Matrix{Float64}`: セルカウントの共分散行列。
  * `directions::Matrix{Float64}`: 仮説検定に使用される方向の行列（[Li, 2012]の式(6)を参照）。これは、[Wang, 2017]の式(5)および(6)に記載された手順に従って計算されます。
  * `N::Int`: 各時点での観測数（デフォルト: 1）
  * `z_k::Vector{Float64}`: 現在の平滑化された値のベクトル。

# 参考文献

Li, J., Tsung, F., & Zou, C. (2012). Directional Control Schemes for Multivariate Categorical Processes. Journal of Quality Technology, 44(2), 136â€“154. https://doi.org/10.1080/00224065.2012.11917889

Wang, J., Li, J., & Su, Q. (2017). Multivariate Ordinal Categorical Process Control Based on Log-Linear Modeling. Journal of Quality Technology, 49(2), 108-122. https://doi.org/10.1080/00224065.2017.11917983
