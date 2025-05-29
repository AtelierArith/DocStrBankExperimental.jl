```julia
findclosestunequal(x::Collection, i::Integer)
```

Return the index of the closest index `n` to `i` for which `x[n] != x[i]`, or `i` if no unequal values of `x` are found.

### Examples

```julia
julia> x = [1, 2, 2, 3, 4]
5-element Vector{Int64}:
 1
 2
 2
 3
 4

julia> findclosestunequal(x, 2)
1

julia> findclosestunequal(x, 3)
4    
```
