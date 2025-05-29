```
has_parent_basis(::Type{<:AbstractBSplineBasis}) -> Bool
has_parent_basis(::AbstractBSplineBasis) -> Bool
```

Trait determining whether a basis has a parent B-spline basis.

This is notably the case for `RecombinedBSplineBasis`, which are derived from regular B-spline bases.
