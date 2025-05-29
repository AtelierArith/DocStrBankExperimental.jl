```
create_independent(x::Union{Cdouble, Vector{Cdouble}}, param::Union{Cdouble,Vector{Cdouble}})
```

The argument `x` is stored as differentiable `Adouble{TbAlloc}` and marked as independent. `param` is marked as parameters on the tape to be changeble without retaping.
