```
crt{T}(b::Vector{T}, a::crt_env{T}) -> T
```

与えられた値 $b$ と `crt_env` によって準備された環境に基づいて、$x \equiv b_i \bmod p_i$ の一意の解（積の剰余に関して）を返します。
