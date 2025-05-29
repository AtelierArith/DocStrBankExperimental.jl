```
divisor(v::Vector{Rational{T}}) where T<:Integer
```

有理数の集合 `v` の最大公約数

#### 例:

```
julia> divisor([1//1, 1//2, 1//3])
6
```
