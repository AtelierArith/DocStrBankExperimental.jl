```
euclDist(arr::Array{T, 1}, h::Array{T, 1}) where {T <: Number}
```

# Description

Euclidean distance.

# Examples

```
julia> euclDist(collect(1:10), fill(5, 10))
9.219544457292887
```

See also: [`bhattDist`](@ref), [`amplitude`](@ref)
