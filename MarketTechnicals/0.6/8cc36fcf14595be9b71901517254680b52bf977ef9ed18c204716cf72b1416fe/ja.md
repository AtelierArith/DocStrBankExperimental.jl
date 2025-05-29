```
obv(ohlcv; price = :Close, v = :Volume)
```

オンバランスボリューム

# 数式

$$
\begin{align*}
\text{OBV}_t = \text{OBV_{t - 1} +
  \begin{cases}
    \text{volume}  & \text{if} P^\text{Close}_t > P^\text{Close}_{t-1} \\
      0            & \text{if} P^\text{Close}_t = P^\text{Close}_{t-1} \\
    -\text{volume} & \text{if} P^\text{Close}_t < P^\text{Close}_{t-1}
  \end{cases}
\end{align*}
$$
