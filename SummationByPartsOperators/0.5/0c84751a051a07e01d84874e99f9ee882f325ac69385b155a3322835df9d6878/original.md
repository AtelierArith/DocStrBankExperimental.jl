```
CubicNonperiodicSemidiscretization(D, Di, split_form, left_bc, right_bc)
```

A semidiscretization of the cubic conservation law     $\partial_t u(t,x) + \partial_x u(t,x)^3 = 0$ with nonperiodic boundary conditions `left_bc(t)`, `right_bc(t)`.

`D` is a first-derivative SBP operator, `Di` an associated dissipation operator or `nothing`, and `split_form::Union{Val(true), Val(false)}` determines whether the canonical split form or the conservative form is used.
