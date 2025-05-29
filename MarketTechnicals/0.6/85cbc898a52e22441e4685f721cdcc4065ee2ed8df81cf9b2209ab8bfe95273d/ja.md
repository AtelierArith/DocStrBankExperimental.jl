```
bollingerbands(ta::TimeArray, ma=20, width=2.0)
```

ボリンジャーバンド

# 公式

$$
\begin{align*}
  \text{上}   & = \text{SMA} + \text{width} \times \sigma(P) \\
  \text{平均} & = \text{SMA} \\
  \text{下} & = \text{SMA} - \text{width} \times \sigma(P)
\end{align*}
$$
