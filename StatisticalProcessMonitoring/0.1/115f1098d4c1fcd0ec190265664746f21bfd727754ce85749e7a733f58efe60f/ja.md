```
MAEWMA(λ, k, value, z::Vector{Float64})
```

多変量適応指数加重移動平均。

新しい観測値 `x` に基づく更新メカニズムは次のように与えられます。

$$
Z_t = (I-\Omega)\cdot Z_{t-1} + \Omega \cdot x_t
$$

、

ここで $Ω = \omega(e)I_p$ は古典的な MEWMA スムージング行列の適応的な一般化です。チャート値は次のように定義されます。

$$
value_t = Z_t' Z_t
$$

。

### 引数

  * `λ::Float64`: EWMA スムージングパラメータの値。
  * `k::Float64`: ハイバー スコアのパラメータの値。
  * `value::Float64`: 統計量の値。 (デフォルト: `0.0`)
  * `z::Vector{Float64}`: スムージングされた観測値のベクトル。

### 参考文献

Mahmoud, M. A., & Zahran, A. R. (2010). A Multivariate Adaptive Exponentially Weighted Moving Average Control Chart. Communications in Statistics - Theory and Methods, 39(4), 606-625. https://doi.org/10.1080/03610920902755813
