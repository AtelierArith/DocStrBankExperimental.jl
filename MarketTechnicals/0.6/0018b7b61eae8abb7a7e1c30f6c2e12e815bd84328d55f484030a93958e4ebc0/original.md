```
kama(ta::TimeArray, n = 10, fn = 2, sn = 30)
```

Kaufman's Adaptive Moving Average

# Arguments

  * `n`: period
  * `fn`: the fastest EMA constant
  * `sn`: the slowest EMA constant

# Formula

$$
\begin{align*}
  \text{KAMA}_t     & = \text{KAMA}_{t-1} + \text{SC} \times (\text{Price} - \text{KAMA}_{t-1}) \\
  \text{SC}         & = (\text{ER} \times (\frac{2}{fn + 1} - \frac{2}{sn + 1}) + \frac{2}{sn + 1})^2 \\
  \text{ER}         & = \frac{Change}{Volatility} \\
  \text{Change}     & = | \text{Price} - \text{Price}_{t-n} | \\
  \text{Volatility} & = \sum_{i}^{n} | \text{Price}_i - \text{Price}_{i - 1} |
\end{align*}
$$
