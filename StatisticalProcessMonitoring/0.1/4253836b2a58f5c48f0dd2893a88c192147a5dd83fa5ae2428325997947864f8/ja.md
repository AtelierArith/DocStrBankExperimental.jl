```
EWMA(λ, value)
```

指数加重移動平均で、設計パラメータ `λ` と初期値 `value` を持ちます。

新しい観測値 `x` に基づく統計量 $C_t$ の更新メカニズムは次のように与えられます。

$$
C_t = (1-λ)\cdot C_{t-1} + λ \cdot x
$$

。

### 引数

  * `λ::Float64`: スムージング定数。デフォルトは `0.1` です。
  * `value::Float64`: EWMA統計量の初期値。デフォルトは `0.0` です。

### 参考文献

Roberts, S. W. (1959). Control Chart Tests Based on Geometric Moving Averages. Technometrics, 1(3), 239-250. https://doi.org/10.1080/00401706.1959.10489860
