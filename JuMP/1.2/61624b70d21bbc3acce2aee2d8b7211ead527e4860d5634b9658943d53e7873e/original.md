```
@NLconstraints(model, args...)
```

Adds multiple nonlinear constraints to model at once, in the same fashion as the [`@NLconstraint`](@ref) macro.

The model must be the first argument, and multiple constraints can be added on multiple lines wrapped in a `begin ... end` block.

The macro returns a tuple containing the constraints that were defined.

# Examples

```julia
@NLconstraints(model, begin
    t >= sqrt(x^2 + y^2)
    [i = 1:2], z[i] <= log(a[i])
end)
```
