```
macd(ta, fast=12, slow=26, signal=9; wilder=false)
```

Moving Average Convergence / Divergence

# Formula

$$
\begin{align*}
  \text{MACD Bar} & = \text{DIF} - \text{DEM} \\
  \text{DIF} & = \text{EMA}(P^\text{Close}, \text{fast}) - \text{EMA}(P^\text{Close}, \text{slow}) \\
  \text{DEM} & = \text{EMA}(\text{DIF}, 9) \tag{signal}
\end{align*}
$$

# Return

`TimeArray` with 3 columns `[:macd, :dif, :signal]`.

If the input is a multi-column `TimeArray`, the new column names will be `[:A_macd, :B_macd, :A_dif, :B_dif, :A_signal, :B_signal]`.
