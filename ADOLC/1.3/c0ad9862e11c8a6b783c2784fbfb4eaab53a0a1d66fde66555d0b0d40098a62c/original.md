```
create_independent(x::Union{Cdouble, Vector{Cdouble}})
```

Marks the argument `x` as independent variable on the tape and create differentiable `Adouble{TbAlloc}` for `x`.
