```
has_diff_equations(sys::AbstractSystem)
```

For a system, returns true if it contain at least one differential equation (i.e. that contain a differential).

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

has_diff_equations(osys1) # returns `true`.
has_diff_equations(osys2) # returns `false`.
```
