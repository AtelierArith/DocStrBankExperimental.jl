```
support(b::BasisFunction) -> UnitRange{Int}
```

Get range of knots supported by the basis function.

Returns the knot range `i:j` such that the basis function support is $t ∈ [t_i, t_j)$.
