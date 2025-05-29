```
points(f::Fun)
```

`f`が値に変換され、再び戻すことができる点のグリッドを返します。

# 例

```jldoctest
julia> f = Fun(x->x^2);

julia> chebypts(n) = [cos((2i+1)pi/2n) for i in 0:n-1];

julia> points(f) ≈ chebypts(ncoefficients(f))
true
```
