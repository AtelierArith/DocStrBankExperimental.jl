```
continued_fraction(a::T, b::T) where T <: Integer
```

Return the continued fraction of the rational `a/b`.

# Example

```julia
julia> continued_fraction(31, 73)
6-element Array{Int64,1}:
 0
 2
 2
 1
 4
 2
```
