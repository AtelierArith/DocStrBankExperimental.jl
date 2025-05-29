```
fixedmass_correlationsum(X [, max_j]; metric = Euclidean(), M = length(X)) → rs, ys
```

A fixed mass algorithm for the calculation of the [`correlationsum`](@ref), and subsequently a fractal dimension $\Delta$, with `max_j` the maximum number of neighbours that should be considered for the calculation.

By default `max_j = clamp(N*(N-1)/2, 5, 32)` with `N` the data length.

## Keyword arguments

  * `M` defines the number of points considered for the averaging of distances, randomly subsampling them from `X`.
  * `metric = Euclidean()` is the distance metric.
  * `start_j = 4` computes the equation below starting from `j = start_j`. Typically the first `j` values have not converged to the correct scaling of the fractal dimension.

## Description

"Fixed mass" algorithms mean that instead of trying to find all neighboring points within a radius, one instead tries to find the max radius containing `j` points. A correlation sum is obtained with this constrain, and equivalently the mean radius containing `k` points. Based on this, one can calculate $\Delta$ approximating the information dimension. The implementation here is due to to [Grassberger1988](@cite), which defines

$$
Ψ(j) - \log N \sim \Delta \times \overline{\log \left( r_{(j)}\right)}
$$

where $\Psi(j) = \frac{\text{d} \log Γ(j)}{\text{d} j}$ is the digamma function, `rs` = $\overline{\log \left( r_{(j)}\right)}$ is the mean logarithm of a radius containing `j` neighboring points, and `ys` = $\Psi(j) - \log N$ ($N$ is the length of the data). The amount of neighbors found $j$ range from 2 to `max_j`. The numbers are also converted to base $2$ from base $e$.

$\Delta$ can be computed by using `linear_region(rs, ys)`.
