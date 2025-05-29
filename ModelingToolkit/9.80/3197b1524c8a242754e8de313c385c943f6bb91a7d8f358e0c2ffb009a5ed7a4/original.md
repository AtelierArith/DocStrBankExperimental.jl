```
has_alg_equations(sys::AbstractSystem)
```

For a system, returns true if it contain at least one algebraic equation (i.e. that does not contain any differentials).

Example:

```julia
using ModelingToolkit
using ModelingToolkit: t_nounits as t, D_nounits as D
@parameters p d
@variables X(t)
eq1 = D(X) ~ p - d*X
eq2 = 0 ~ p - d*X
@named osys1 = ODESystem([eq1], t)
@named osys2 = ODESystem([eq2], t)

has_alg_equations(osys1) # returns `false`.
has_alg_equations(osys2) # returns `true`.
```
