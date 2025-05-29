```
woodiespivots(ohlc::TimeArray)
```

ウッディのピボット

# フォーミュラ

$$
\begin{align*}
  \text{Range}   & = P^{high}_{t-1} - P^{low}_{t-1} \\
  R_4            & = S_4 + \text{Range} \tag{not implemented} \\
  R_3            & = R_1 + \text{Range} \\
  R_2            & = \text{Pivot}_t + \text{Range} \\
  R_1            & = 2 \text{Pivot}_t - P^{low}_{t-1} \\
  \text{Pivot}_t & =
      frac{P^{high}_{t-1} + P^{low}_{t-1} + 2 P^{open}_t}{4} \\
  S_1            & = 2 \text{Pivot}_t - P^{high}_{t-1} \\
  S_2            & = \text{Pivot}_t - \text{Range} \\
  S_3            & = S1 - \text{Range} \\
  S_4            & = S3 - \text{Range} \tag{not implemented}
\end{align*}
$$
