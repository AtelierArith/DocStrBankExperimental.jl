```
ema(ta::TimeArray, n, wilder = false)
ema(A::Array, n, wilder = false)
```

指数移動平均

別名：指数加重移動平均 (EWMA)

# 公式

$$
k
$$

を重み減少の度合いとします。

パラメータ `wilder` が `true` の場合、$k = \frac{1}{n}$、そうでない場合は $k = \frac{2}{n + 1}$ です。

$$
\text{EMA}_t = k \times P_t + (1 - k) \times \text{EMA}_{t - 1}
$$
