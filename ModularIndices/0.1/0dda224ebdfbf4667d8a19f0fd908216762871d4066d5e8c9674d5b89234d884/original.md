```
Mod(idx)
```

Construct a modular (periodic) index.

# Examples

```jldoctest
julia> A = 1:3
1:3

julia> A[Mod(4)]
1

julia> A[Mod(2:4)]
3-element Array{Int64,1}:
 2
 3
 1

```
