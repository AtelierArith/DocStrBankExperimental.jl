```
Fun(s::Space, coefficients::AbstractVector)
```

指定された `coefficients` を持つ `Fun` を空間 `s` で返します

# 例

```jldoctest
julia> f = Fun(Fourier(), [1,1]);

julia> f(0.1) == 1 + sin(0.1)
true

julia> f = Fun(Chebyshev(), [1,1]);

julia> f(0.1) == 1 + 0.1
true
```
