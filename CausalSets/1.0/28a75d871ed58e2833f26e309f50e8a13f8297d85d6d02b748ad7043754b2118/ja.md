```
TorusManifold{N}(spatial_size::Float64) <: ConformallyTimesliceableManifold{N}
```

多様体 $\mathbb{R} \times T^{N-1}$ は、$T^{N-1}$ が `spatial_size` で指定されたサイズの $N-1$ 次元トーラスである。

座標 $N$-タプルは $(t, x_1, \cdots, x_{N-1})$ であり、$x_i$ は `-spatial_size/2` から `spatial_size/2` の範囲を取る。計量はミンコフスキー型である：

$$
\begin{aligned}
\mathrm{d}s^2 = - \mathrm{d} t^2 + \sum_i \mathrm{d} x_i^2
\end{aligned}
$$

ここで、$\mathrm{d} x_i$ はトーラス多様体上での `spatial_size` に関する剰余を用いた引き算によって定義される。
