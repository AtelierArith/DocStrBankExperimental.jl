```
taylor!(
    u,
    ::Val{K},
    H::CompiledHomotopy,
    x,
    p = nothing,
)
```

Compute the Taylor series order order `K` of $u = H(x,t,p)$.
