```
TorusManifold{N}(spatial_size::Float64) <: ConformallyTimesliceableManifold{N}
```

The manifold $\mathbb{R} \times T^{N-1}$, where $T^{N-1}$ is the $N-1$-dimensional torus with the size specified by `spatial_size`.

The coordinate $N$-tuple is $(t, x_1, \cdots, x_{N-1})$, where $x_i$ ranges from `-spatial_size/2` to `spatial_size/2`. The metric is Minkowskian:

$$
\begin{aligned}
\mathrm{d}s^2 = - \mathrm{d} t^2 + \sum_i \mathrm{d} x_i^2
\end{aligned}
$$

where $\mathrm{d} x_i$ is defined by subtraction modulo `spatial_size` on the torus manifold.
