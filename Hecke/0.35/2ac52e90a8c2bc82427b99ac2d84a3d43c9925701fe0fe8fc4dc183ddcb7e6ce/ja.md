```
crt_inv(a::T, crt_env{T}) -> Vector{T}
```

与えられた $\code{crt_env}$ と要素 $a$ に対して、すべての $i$ に対して $a \bmod pr_i$ の剰余データを返します。これは本質的に $\code{crt}$ 関数の逆です。
