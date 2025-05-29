```
unbatch(x)
```

Reverse of the [`batch`](@ref) operation, unstacking the last dimension of the array `x`.

See also [`unstack`](@ref) and [`chunk`](@ref).

# Examples

```jldoctest
julia> unbatch([1 3 5 7;
                2 4 6 8])
4-element Vector{Vector{Int64}}:
 [1, 2]
 [3, 4]
 [5, 6]
 [7, 8]
```
