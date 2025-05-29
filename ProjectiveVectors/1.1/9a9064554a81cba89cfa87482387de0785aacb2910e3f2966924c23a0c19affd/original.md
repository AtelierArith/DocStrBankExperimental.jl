```
homvars(z::PVector{T,N})
```

Return the indices of the homogenization variables.

## Example

```julia-repl
julia> v = PVector([4, 5, 6], [2, 3], [1, 2])
PVector{Int64, 3}:
 [4, 5, 6] × [2, 3] × [1, 2]

 julia> homvars(v)
 (3, 5, 7)
```
