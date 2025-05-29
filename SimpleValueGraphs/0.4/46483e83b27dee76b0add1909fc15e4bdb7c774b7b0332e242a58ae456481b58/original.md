```
get_edgeval(g::AbstractValGraph, s, d, key)
```

Return the value associated with the edge `s -> d` for the key `key` in `g`.

Throw an exception if the graph does not contain such an edge or if the key is not a valid edge key.

For graphs that only have one value per edge, `key` can be omitted.

### See also

[`get_edgeval_or`](@ref), [`set_edgeval!`](@ref)

### Examples

```jldoctest
julia> gv = ValDiGraph(path_digraph(3), edgeval_types=(a=Float64,), edgeval_init=(s, d) -> (rand(MersenneTwister(0)),))
{3, 2} directed ValDiGraph with
              eltype: Int64
  vertex value types: ()
    edge value types: (a = Float64,)
   graph value types: ()

julia> get_edgeval(gv, 1, 2, :a)
0.8236475079774124

julia> get_edgeval(gv, 1, 2, 1)
0.8236475079774124

julia> get_edgeval(gv, 1, 2)
0.8236475079774124

julia> get_edgeval(gv, 1, 3)
ERROR: No such edge

julia> get_edgeval(gv, 1, 2, :b)
ERROR: b is not a valid edge key for this graph.
```
