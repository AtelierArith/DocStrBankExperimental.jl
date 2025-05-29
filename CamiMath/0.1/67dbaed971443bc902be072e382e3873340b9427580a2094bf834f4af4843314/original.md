```
normalize_rationals(v::Vector{Rational{T}}) where T<:Integer
```

Numerators separated from divisor

#### Example:

```
julia> normalize_rationals([1//1, 1//2, 1//3])
([6, 3, 2], 6)
```
