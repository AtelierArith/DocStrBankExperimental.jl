```
floorpivots(ohlc::TimeArray)
```

Floor Trader Pivots

# Formula

$$
\begin{align*}

  R_3            & = \text{Pivot}_t + (R_2 - S_1) \\
  R_2            & = \text{Pivot}_t + (R_1 - S_1) \\
  R_1            & = 2 \text{Pivot}_t - P^{low}_{t-1} \\
  \text{Pivot}_t & = P^{typical}_{t-1} =
      \frac{P^{high}_{t-1} + P^{low}_{t-1} + P^{close}_{t-1}}{3} \\
  S_1            & = 2 \text{Pivot}_t - P^{high}_{t-1} \\
  S_2            & = \text{Pivot}_t - (R_1 - S_1) \\
  S_3            & = \text{Pivot}_t - (R_2 - S_1)

\end{align*}
$$
