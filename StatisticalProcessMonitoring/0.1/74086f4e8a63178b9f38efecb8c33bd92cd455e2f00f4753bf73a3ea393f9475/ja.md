```
AEWMA(λ, k, value)
```

適応的指数加重移動平均で、設計パラメータ `λ`、`k`、および初期値 `value` を持ちます。

新しい観測値 `x` に基づく統計量 $C_t$ の更新メカニズムは次のように与えられます。

$$
C_t = (1-\phi(e))\cdot C_{t-1} + \phi(e) \cdot x
$$

、

ここで、$\phi(e)$ はハーバースコア関数に基づく予測誤差関数です。

### 引数

  * `λ::Float64`: スムージング定数。デフォルトは `0.1` です。
  * `k::Float64`: ハーバースコアにおける閾値。デフォルトは `3.0` です。
  * `value::Float64`: 統計量の初期値。デフォルトは 0.0 です。

### 参考文献

Capizzi, G. & Masarotto, G. (2003). An Adaptive Exponentially Weighted Moving Average Control Chart. Technometrics, 45(3), 199-207.
