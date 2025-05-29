```
divisor(v::Vector{Rational{T}}) where T<:Integer
```

Greatest common denominator of the set of rational numbers `v`

#### Example:

```
julia> divisor([1//1, 1//2, 1//3])
6
```
