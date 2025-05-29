```
points(s::Space,n::Integer)
```

グリッド上の約 `n` 点の配列を返します。このグリッドの値から空間 `s` の係数への変換が存在します。

# 例

```jldoctest
julia> chebypts(n) = [cos((2i+1)pi/2n) for i in 0:n-1];

julia> points(Chebyshev(), 4) ≈ chebypts(4)
true
```
