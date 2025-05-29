```
bhattDist(arr::Array{T, 1}, h::Array{T, 1}) where {T <: Number}
```

# Description

Bhattacharyya distance.

# Examples

```
julia> bhattDist(collect(1:10), fill(5, 10))
-3.936532135073928
```

See also: [`euclDist`](@ref), [`amplitude`](@ref)
