```
extrapolate(f::Fun,x)
```

`f`の定義域から`x`への外挿を返します。

# 例

```jldoctest
julia> f = Fun(x->x^2)
Fun(Chebyshev(), [0.5, 0.0, 0.5])

julia> extrapolate(f, 2) # 2は定義域-1..1の外にあります
4.0
```
