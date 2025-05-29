```
ValMatrix(g::AbstractGraph, key, zero_value)
```

Construct a new `ValMatrix` view for a graph `g` where the values are the edge values specified by `key`. Entries that are not in the graph are represented by `zero_value` in the matrix.

### See also

[`AdjacencyMatrix`](@ref), [`adjacency_matrix`](@ref), [`weights`](@ref)

### Examples

```jldoctest
julia> gv = ValDiGraph(path_digraph(3),  edgeval_types=(a=Float64, b=String), edgeval_init=(s, d) -> (rand(MersenneTwister(0)), "$s-$d"))
{3, 2} directed ValDiGraph with
              eltype: Int64
  vertex value types: ()
    edge value types: (a = Float64, b = String)
   graph value types: ()

julia> ValMatrix(gv, 1, 0.0)
3×3 ValMatrix{Float64, ValDiGraph{Int64, Tuple{}, NamedTuple{(:a, :b), Tuple{Float64, String}}, Tuple{}, Tuple{}, NamedTuple{(:a, :b), Tuple{Vector{Vector{Float64}}, Vector{Vector{String}}}}}, 1}:
 0.0  0.823648  0.0
 0.0  0.0       0.823648
 0.0  0.0       0.0

julia> ValMatrix(gv, :b, nothing)
3×3 ValMatrix{Union{Nothing, String}, ValDiGraph{Int64, Tuple{}, NamedTuple{(:a, :b), Tuple{Float64, String}}, Tuple{}, Tuple{}, NamedTuple{(:a, :b), Tuple{Vector{Vector{Float64}}, Vector{Vector{String}}}}}, :b}:
 nothing  "1-2"    nothing
 nothing  nothing  "2-3"
 nothing  nothing  nothing
```
