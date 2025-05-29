```
ncoefficients(f::Fun) -> Integer
```

ファンクションの係数の数を返します

# 例

```jldoctest
julia> f = Fun(x->x^2)
Fun(Chebyshev(), [0.5, 0.0, 0.5])

julia> ncoefficients(f)
3
```
