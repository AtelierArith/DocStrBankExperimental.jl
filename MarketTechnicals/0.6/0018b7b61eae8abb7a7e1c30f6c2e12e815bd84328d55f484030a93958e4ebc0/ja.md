```
kama(ta::TimeArray, n = 10, fn = 2, sn = 30)
```

カウフマンの適応移動平均

# 引数

  * `n`: 期間
  * `fn`: 最も速いEMA定数
  * `sn`: 最も遅いEMA定数

# 公式

$$
\begin{align*}
  \text{KAMA}_t     & = \text{KAMA}_{t-1} + \text{SC} \times (\text{Price} - \text{KAMA}_{t-1}) \\
  \text{SC}         & = (\text{ER} \times (\frac{2}{fn + 1} - \frac{2}{sn + 1}) + \frac{2}{sn + 1})^2 \\
  \text{ER}         & = \frac{Change}{Volatility} \\
  \text{Change}     & = | \text{Price} - \text{Price}_{t-n} | \\
  \text{Volatility} & = \sum_{i}^{n} | \text{Price}_i - \text{Price}_{i - 1} |
\end{align*}
$$
