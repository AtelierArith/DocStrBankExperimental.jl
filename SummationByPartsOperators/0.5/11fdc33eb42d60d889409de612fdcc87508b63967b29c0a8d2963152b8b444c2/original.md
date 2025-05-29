```
BurgersNonperiodicSemidiscretization(D, Di, split_form, left_bc, right_bc)
```

A semidiscretization of Burgers' equation     $\partial_t u(t,x) + \partial_x \frac{u(t,x)^2}{2} = 0$ with boundary conditions `left_bc(t)`, `right_bc(t)`.

`D` is a first-derivative SBP operator, `Di` an associated dissipation operator or `nothing`, and `split_form::Union{Val(true), Val(false)}` determines whether the canonical split form or the conservative form is used.
