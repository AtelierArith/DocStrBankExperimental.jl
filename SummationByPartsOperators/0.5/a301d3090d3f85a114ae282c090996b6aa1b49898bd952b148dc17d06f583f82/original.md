```
PeriodicUpwindOperators
PeriodicUpwindOperators(D_minus, D_central, D_plus)
```

A struct bundling the individual operators available for periodic upwind SBP operators. The individual operators are available as `D.minus`, `D.plus` (and optionally `D.central`, if provided), where `D::PeriodicUpwindOperators`.

The combined struct behaves as much as possible as an operator itself as long as no ambiguities arise. For example, upwind operators need to use the same grid and mass matrix, so [`mass_matrix`](@ref), [`grid`](@ref), [`xmin`](@ref), [`xmax`](@ref) etc. are available but `mul!` is not.

It is recommended to construct an instance of `PeriodicUpwindOperators` using [`upwind_operators`](@ref). An instance can also be constructed manually by passing the operators in the order `D_minus, D_central, D_plus`.

See also [`upwind_operators`](@ref), [`UpwindOperators`](@ref)
