```
structures(γ)
```

Return the individual structures of a (possibly composite) variogram as a tuple. The structures are the total nugget, and the coefficients (or contributions) for for the remaining non-trivial structures after normalization (i.e. sill=1, nugget=0).

## Examples

```julia
γ₁ = GaussianVariogram(nugget=1, sill=2)
γ₂ = SphericalVariogram(nugget=2, sill=3)

structures(2γ₁ + 3γ₂)
```
