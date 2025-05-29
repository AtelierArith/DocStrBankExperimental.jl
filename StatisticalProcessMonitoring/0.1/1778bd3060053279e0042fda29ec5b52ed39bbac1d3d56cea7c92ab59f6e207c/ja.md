```
DiagMEWMA(Λ, value)
```

対角スムージング行列 `Λ` と初期値 `value` を持つ指数加重移動平均。

新しい観測 `x` に基づく更新メカニズムは次のように与えられます。

$$
Z_t = (I-Λ)Z_{t-1} + Λ x_t
$$

、

チャート値は次のように定義されます。

$$
C_t = Z_t' Λ^{-1} Z_t
$$

。

### 引数

  * `Λ::Vector{Float64}`: スムージング定数のベクトル。
  * `value::Float64`: 統計量の現在の値 (デフォルト = 0.0)。
  * `z::Vector{Float64}`: スムーズされた観測のベクトル (デフォルト: `zeros(length(Λ))`)。
  * `inv_Σz::Matrix{Float64}`: 制御変数の共分散行列の逆行列。

### 参考文献

Lowry, C. A., Woodall, W. H., Champ, C. W., & Rigdon, S. E. (1992). A Multivariate Exponentially Weighted Moving Average Control Chart. Technometrics, 34(1), 46-53. https://doi.org/10.1080/00401706.1992.10485232
