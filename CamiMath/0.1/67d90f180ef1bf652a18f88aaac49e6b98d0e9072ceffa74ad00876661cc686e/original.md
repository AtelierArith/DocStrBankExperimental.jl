```
canonical_partitions(n::Int, [m=0 , [sense=rev [; header=true]]])
```

Canonical partition of `n` in parts of maximum size `m` (`m` = 0 for any size)

`sense` : regular ([`reg`](@ref)) or reverse ([`rev`](@ref))     `header` : unit partition included in output

#### Examples:

```
julia> canonical_partitions(6, 0, reg; header=true)
6-element Vector{Vector{Int64}}:
 [6]
 [5, 1]
 [4, 2]
 [3, 3]
 [2, 2, 2]
 [1, 1, 1, 1, 1, 1]

julia> canonical_partitions(6; header=true)
6-element Vector{Vector{Int64}}:
 [1, 1, 1, 1, 1, 1]
 [2, 2, 2]
 [3, 3]
 [4, 2]
 [5, 1]
 [6]

julia> canonical_partitions(6)
6-element Vector{Vector{Int64}}:
 [1, 1, 1, 1, 1, 1]
 [2, 2, 2]
 [3, 3]
 [4, 2]
 [5, 1]
 [6]

julia> o = canonical_partitions(9, 2); println(o)
[2, 2, 2, 2, 1]

julia> o = canonical_partitions(9, 3); println(o)
[3, 3, 3]
```
