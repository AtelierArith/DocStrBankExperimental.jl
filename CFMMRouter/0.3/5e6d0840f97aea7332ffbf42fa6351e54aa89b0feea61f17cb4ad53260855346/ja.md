```
BasketLiquidation(i, Δin)
```

ル liquidation 目的のルーティング問題、

$$
    \Psi_i - \mathbf{I}(\Psi_{-i} + Δ^\mathrm{in}_{-i} = 0, ~ \Psi_i \geq 0),
$$

ここで `i` は希望する出力トークンであり、`Δin` は清算されるトークンのバスケットです。
