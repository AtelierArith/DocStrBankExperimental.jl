```
Pℤ{P, X}
```

ℤₚ[X] の多項式。

# 例

```jldoctest
julia> a = Pℤ{3, :x}(:(1 + x + 2x^2))
1 + x + 2x^2

julia> b = Pℤ{3, :x}("1 + x + 2x^2")
1 + x + 2x^2

julia> c = Pℤ{3}(2)
2

julia> d = Pℤ{3}(5)
2

julia> e = Pℤ₂([1,0,0,1,1,0,1])
1 + x^3 + x^4 + x^6
```
