```
VariableLinearAdvectionPeriodicSemidiscretization(D, Di, a, split_form)
```

A semidiscretization of the linear advection equation     $\partial_t u(t,x) + \partial_x ( a(x) u(t,x) ) = 0$ with periodic boundary conditions.

`D` is a periodic SBP derivative operator, `Di` an associated dissipation operator or `nothing`, `a(x)` the variable coefficient, and `split_form::Union{Val(false), Val(true)}` determines whether the canonical split form or the conservative form should be used.
