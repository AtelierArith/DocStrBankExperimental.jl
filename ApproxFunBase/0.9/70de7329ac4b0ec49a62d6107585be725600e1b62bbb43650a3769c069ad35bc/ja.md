```
space(f::Fun)
```

`f`の空間を返します。

# 例

```jldoctest
julia> f = Fun(x->x^2)
Fun(Chebyshev(), [0.5, 0.0, 0.5])

julia> space(f)
Chebyshev()
```
