```
grouped_nearest(tree::KDTree, siteindex::Int, nsites::Int; atol=1e-8)
```

Find the `nsites` closest vertices to `siteindex`, and group them by distance. Difference of the distances smaller than the `atol` (default is `1e-8`) are treated as the same Returns a [`DistanceGroup`](@ref) instance.

```jldoctest; setup=:(using BloqadeLattices)
julia> atoms = generate_sites(HoneycombLattice(), 5, 5);

julia> tree = make_kdtree(atoms);

julia> gn = grouped_nearest(tree, 23, 20)
DistanceGroup([23, 14, 22, 24, 15, 13, 21, 25, 33, 31, 12, 16, 32, 4, 6, 34, 26, 17, 5, 41], [1, 2, 5, 11, 14, 18, 21])

julia> gn[0]  # the 0-th nearest neighbor is defined by vertex itself
1-element Vector{Int64}:
 23

julia> gn[1]  # nearest neighbors
3-element Vector{Int64}:
 14
 22
 24

julia> gn[2]  # second nearest neighbors
6-element Vector{Int64}:
 15
 13
 21
 25
 33
 31
```
