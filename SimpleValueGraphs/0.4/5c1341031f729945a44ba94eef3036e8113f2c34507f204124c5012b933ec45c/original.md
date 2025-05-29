```
get_edgeval(g::AbstractValGraph, s, d, :)
```

Return all values associated with the edge `s -> d` in `g`.

Throw an exception if the graph does not contain such an edge.

### See also

[`get_edgeval_or`](@ref), [`set_edgeval!`](@ref)

### Examples

```jldoctest
julia> gv = ValDiGraph(path_digraph(3), edgeval_types=(a=Float64, b=Int), edgeval_init=(s, d) -> (rand(MersenneTwister(0)), 10))
{3, 2} directed ValDiGraph with
              eltype: Int64
  vertex value types: ()
    edge value types: (a = Float64, b = Int64)
   graph value types: ()

julia> get_edgeval(gv, 1, 2, :)
(a = 0.8236475079774124, b = 10)

julia> get_edgeval(gv, 1, 3, :)
ERROR: Values not found
```
