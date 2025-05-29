```
taylor!(
    u,
    ::Val{K},
    F::CompiledSystem,
    x,
    p = nothing,
)
```

Compute the Taylor series order order `K` of $u = F(x,p)$.
