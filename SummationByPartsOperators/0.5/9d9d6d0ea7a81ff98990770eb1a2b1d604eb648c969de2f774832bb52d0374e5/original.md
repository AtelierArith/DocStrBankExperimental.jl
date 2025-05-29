```
BurgersPeriodicSemidiscretization(D, Di, split_form)
```

A semidiscretization of Burgers' equation     $\partial_t u(t,x) + \partial_x \frac{u(t,x)^2}{2} = 0$ with periodic boundary conditions.

`D` is a first-derivative SBP operator, `Di` an associated dissipation operator or `nothing`, and `split_form::Union{Val(true), Val(false)}` determines whether the canonical split form or the conservative form is used.
