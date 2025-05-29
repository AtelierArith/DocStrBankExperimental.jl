```
MinkowskiManifold{N} <: ConformallyMinkowskianManifold{N}
```

A Minkowski manifold with one time dimension and $N - 1$ spatial dimensions. The coordinate $N$-tuple is $(t, x_1, \cdots, x_{N-1})$, and the metric is

$$
\begin{aligned}
\mathrm{d}s^2 = - \mathrm{d} t^2 + \sum_i \mathrm{d} x_i^2
\end{aligned}
$$
