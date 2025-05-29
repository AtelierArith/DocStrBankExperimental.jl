```
coeff(a::MPoly{T}, exps::Vector{Int}) where T <: RingElement
```

与えられた指数ベクトルを持つ項の係数を返します。該当する項がない場合はゼロを返します。
