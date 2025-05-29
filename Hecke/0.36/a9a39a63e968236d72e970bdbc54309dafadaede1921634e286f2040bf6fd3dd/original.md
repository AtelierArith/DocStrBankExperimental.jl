```
crt{T}(b::Vector{T}, a::crt_env{T}) -> T
```

Given values in $b$ and the environment prepared by `crt\_env`, return the unique (modulo the product) solution to $x \equiv b_i \bmod p_i$.
