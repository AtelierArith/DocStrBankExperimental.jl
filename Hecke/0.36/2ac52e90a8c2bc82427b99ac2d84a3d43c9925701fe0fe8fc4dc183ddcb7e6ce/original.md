```
crt_inv(a::T, crt_env{T}) -> Vector{T}
```

Given a $\code{crt_env}$ and an element $a$, return the modular data $a \bmod pr_i$ for all $i$. This is essentially the inverse to the $\code{crt}$ function.
