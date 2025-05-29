```
structures(cov)
```

Return the individual structures of a (possibly composite) covariance as a tuple. The structures are the total nugget, and the coefficients (or contributions) for for the remaining non-trivial structures after normalization (i.e. sill=1, nugget=0).

## Examples

```julia
cov₁ = GaussianCovariance(nugget=1, sill=2)
cov₂ = SphericalCovariance(nugget=2, sill=3)

structures(2cov₁ + 3cov₂)
```
