```
CubicPeriodicSemidiscretization(D, Di, split_form)
```

A semidiscretization of the cubic conservation law     $\partial_t u(t,x) + \partial_x u(t,x)^3 = 0$ with periodic boundary conditions.

`D` is a first-derivative SBP operator, `Di` an associated dissipation operator or `nothing`, and `split_form::Union{Val(true), Val(false)}` determines whether the canonical split form or the conservative form is used.
