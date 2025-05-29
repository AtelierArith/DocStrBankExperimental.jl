```
root_lattice(R::Vector{Tuple{Symbol,Int}}) -> ZZLat
```

Return the root lattice of type `R` (see [`root_lattice`](@ref)).

#Example

```jldoctest
julia> root_lattice([(:A,2),(:A,1)])
Integer lattice of rank 3 and degree 3
with gram matrix
[ 2   -1   0]
[-1    2   0]
[ 0    0   2]

```
