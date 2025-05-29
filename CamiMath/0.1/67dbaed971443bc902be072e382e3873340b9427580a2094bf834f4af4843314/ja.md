```
normalize_rationals(v::Vector{Rational{T}}) where T<:Integer
```

分母から分子を分離する

#### 例:

```
julia> normalize_rationals([1//1, 1//2, 1//3])
([6, 3, 2], 6)
```
