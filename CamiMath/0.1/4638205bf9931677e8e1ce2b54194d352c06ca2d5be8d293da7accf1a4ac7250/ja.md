```
numerators(v::Vector{Rational{T}}) where T<:Integer
```

有理数の集合 `v` の標準除数の分子

#### 例:

```
julia> numerators([1//1, 1//2, 1//3])
3-element Vector{Int64}:
 6
 3
 2
```
