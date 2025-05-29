```julia
allgraphs(
    n::Vector{Int64};
    connected
) -> Vector{Tuple{Vector{Pair{Int64, Int64}}, Float64}}

```

Generates all unique topologies for a given vertex specification. It takes in a vector where `n[k]` is the number of vertices of degree `k`. By default, it generates connected graphs, unconnected can be computed by setting the keyword argument `connected=false`.

Returns a Vector of Tuples `(Vector{Edge}, S)` with `Edge` a `Tuple{Int64,Int64}` representing an edge in the graph and `S::Float64` the corresponding symmetry factor.

## Example

For input `n = [2, 0, 0, 2]` (2 vertices of degree 1, 2 vertex of degree 4):

```jldoctest
julia> using GraphCombinations

julia> allgraphs([2, 0, 0, 2])
3-element Vector{Tuple{Vector{Pair{Int64, Int64}}, Float64}}:
 ([1 => 3, 2 => 3, 3 => 4, 3 => 4, 4 => 4], 4.0)
 ([1 => 3, 2 => 4, 3 => 3, 3 => 4, 4 => 4], 4.0)
 ([1 => 3, 2 => 4, 3 => 4, 3 => 4, 3 => 4], 6.0)
```
