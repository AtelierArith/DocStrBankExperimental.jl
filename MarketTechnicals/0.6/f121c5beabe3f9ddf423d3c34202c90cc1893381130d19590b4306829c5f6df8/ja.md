```
macd(ta, fast=12, slow=26, signal=9; wilder=false)
```

移動平均収束 / 発散

# 公式

$$
\begin{align*}
  \text{MACD Bar} & = \text{DIF} - \text{DEM} \\
  \text{DIF} & = \text{EMA}(P^\text{Close}, \text{fast}) - \text{EMA}(P^\text{Close}, \text{slow}) \\
  \text{DEM} & = \text{EMA}(\text{DIF}, 9) \tag{signal}
\end{align*}
$$

# 戻り値

`TimeArray` は 3 列 `[:macd, :dif, :signal]` を持ちます。

入力が複数列の `TimeArray` の場合、新しい列名は `[:A_macd, :B_macd, :A_dif, :B_dif, :A_signal, :B_signal]` になります。
