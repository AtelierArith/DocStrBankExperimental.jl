```
@NLconstraint(model::GenericModel, expr)
```

Add a constraint described by the nonlinear expression `expr`. See also [`@constraint`](@ref).

!!! compat
    This macro is part of the legacy nonlinear interface. Consider using the new nonlinear interface documented in [Nonlinear Modeling](@ref). In most cases, you can replace `@NLconstraint` with [`@constraint`](@ref).


## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> @NLconstraint(model, sin(x) <= 1)
sin(x) - 1.0 ≤ 0

julia> @NLconstraint(model, [i = 1:3], sin(i * x) <= 1 / i)
3-element Vector{NonlinearConstraintRef{ScalarShape}}:
 (sin(1.0 * x) - 1.0 / 1.0) - 0.0 ≤ 0
 (sin(2.0 * x) - 1.0 / 2.0) - 0.0 ≤ 0
 (sin(3.0 * x) - 1.0 / 3.0) - 0.0 ≤ 0
```
