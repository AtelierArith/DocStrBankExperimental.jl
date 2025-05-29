```
MinkowskiManifold{N} <: ConformallyMinkowskianManifold{N}
```

時間次元が1つと$N - 1$の空間次元を持つミンコフスキー多様体。座標$N$-タプルは$(t, x_1, \cdots, x_{N-1})$であり、計量は次のようになります。

$$
\begin{aligned}
\mathrm{d}s^2 = - \mathrm{d} t^2 + \sum_i \mathrm{d} x_i^2
\end{aligned}
$$
