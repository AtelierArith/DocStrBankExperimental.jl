```
LKJ(d, η)
```

```julia
d::Int   dimension
η::Real  positive shape
```

The [LKJ](https://doi.org/10.1016/j.jmva.2009.04.008) distribution is a distribution over $d\times d$ real correlation matrices (positive-definite matrices with ones on the diagonal). If $\mathbf{R}\sim \textrm{LKJ}_{d}(\eta)$, then its probability density function is

$$
f(\mathbf{R};\eta) = \left[\prod_{k=1}^{d-1}\pi^{\frac{k}{2}}
\frac{\Gamma\left(\eta+\frac{d-1-k}{2}\right)}{\Gamma\left(\eta+\frac{d-1}{2}\right)}\right]^{-1}
|\mathbf{R}|^{\eta-1}.
$$

If $\eta = 1$, then the LKJ distribution is uniform over [the space of correlation matrices](https://www.jstor.org/stable/2684832).

!!! note
    if a Cholesky factor of the correlation matrix is desired, it is more efficient to use [`LKJCholesky`](@ref), which avoids factorizing the matrix.

