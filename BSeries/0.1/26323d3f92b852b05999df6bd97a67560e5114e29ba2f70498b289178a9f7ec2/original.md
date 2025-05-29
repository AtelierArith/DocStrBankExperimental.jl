```
TruncatedBSeries
```

A struct that can describe B-series of both numerical integration methods (where the coefficient of the empty tree is unity) and right-hand sides of an ordinary differential equation and perturbations thereof (where the coefficient of the empty tree is zero) up to a prescribed [`order`](@ref).

Generally, this kind of `struct` should be constructed via [`bseries`](@ref) or one of the other functions returning a B-series, e.g., [`modified_equation`](@ref) or [`modifying_integrator`](@ref).
