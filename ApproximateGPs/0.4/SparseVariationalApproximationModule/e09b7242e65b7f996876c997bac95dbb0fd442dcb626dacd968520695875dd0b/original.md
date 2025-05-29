```
SparseVariationalApproximation(
    ::Parametrization, fz::FiniteGP, q::AbstractMvNormal
) where {Parametrization}
```

Produce a `SparseVariationalApproximation{Parametrization}`, which packages the prior over the pseudo-points, `fz`, and the approximate posterior at the pseudo-points, `q`, together into a single object.

The `Parametrization` determines the precise manner in which `q` and `fz` are interpreted. Existing parametrizations include [`Centered`](@ref) and [`NonCentered`](@ref).
