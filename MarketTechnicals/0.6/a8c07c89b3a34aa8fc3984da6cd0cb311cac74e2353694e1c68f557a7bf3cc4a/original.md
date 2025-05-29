```
ema(ta::TimeArray, n, wilder = false)
ema(A::Array, n, wilder = false)
```

Exponemtial Moving Average

A.k.a. exponentially weighted moving average (EWMA)

# Formula

Let $k$ denote the degree of weighting decrease.

If parameter `wilder` is `true`, $k = \frac{1}{n}$, else $k = \frac{2}{n + 1}$.

$$
\text{EMA}_t = k \times P_t + (1 - k) \times \text{EMA}_{t - 1}
$$
