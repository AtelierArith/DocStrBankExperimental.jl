```
@NLconstraint(m::Model, expr)
```

Add a constraint described by the nonlinear expression `expr`. See also [`@constraint`](@ref). For example:

```julia
@NLconstraint(model, sin(x) <= 1)
@NLconstraint(model, [i = 1:3], sin(i * x) <= 1 / i)
```
