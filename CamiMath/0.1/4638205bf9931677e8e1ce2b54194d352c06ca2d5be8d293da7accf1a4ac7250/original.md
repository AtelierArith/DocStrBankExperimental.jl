```
numerators(v::Vector{Rational{T}}) where T<:Integer
```

Numerators for the standard devisor of the set of rational numbers `v`

#### Example:

```
julia> numerators([1//1, 1//2, 1//3])
3-element Vector{Int64}:
 6
 3
 2
```
