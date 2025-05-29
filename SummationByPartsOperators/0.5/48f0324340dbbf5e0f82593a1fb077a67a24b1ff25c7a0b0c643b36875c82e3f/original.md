```
VariableLinearAdvectionNonperiodicSemidiscretization(D, Di, a, split_form,
                                                     left_bc, right_bc)
```

A semidiscretization of the linear advection equation     $\partial_t u(t,x) + \partial_x ( a(x) u(t,x) ) = 0$ with boundary conditions `left_bc(t)`, `right_bc(t)`.

`D` is an SBP derivative operator, `Di` an associated dissipation operator or `nothing`, `a(x)` the variable coefficient, and `split_form::Union{Val(false), Val(true)}` determines whether the canonical split form or the conservative form should be used.
