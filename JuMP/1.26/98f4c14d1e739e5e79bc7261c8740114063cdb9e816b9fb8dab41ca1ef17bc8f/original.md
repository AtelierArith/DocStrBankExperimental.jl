```
@NLconstraints(model, args...)
```

Adds multiple nonlinear constraints to model at once, in the same fashion as the [`@NLconstraint`](@ref) macro.

The model must be the first argument, and multiple constraints can be added on multiple lines wrapped in a `begin ... end` block.

The macro returns a tuple containing the constraints that were defined.

!!! compat
    This macro is part of the legacy nonlinear interface. Consider using the new nonlinear interface documented in [Nonlinear Modeling](@ref). In most cases, you can replace `@NLconstraints` with [`@constraints`](@ref).


## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @variable(model, y);

julia> @variable(model, t);

julia> @variable(model, z[1:2]);

julia> a = [4, 5];

julia> @NLconstraints(model, begin
           t >= sqrt(x^2 + y^2)
           [i = 1:2], z[i] <= log(a[i])
       end)
((t - sqrt(x ^ 2.0 + y ^ 2.0)) - 0.0 ≥ 0, NonlinearConstraintRef{ScalarShape}[(z[1] - log(4.0)) - 0.0 ≤ 0, (z[2] - log(5.0)) - 0.0 ≤ 0])
```
