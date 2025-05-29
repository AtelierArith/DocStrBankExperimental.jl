```
get_edgeval_or(g::ValGraph, s, d, alternative)
get_edgeval_or(g::ValDiGraph, s, d, alternative)
get_edgeval_or(g::ValOutDiGraph, s, d, alternative)
```

Return all values associated with the edge `s -> d` in `g`.

If there is no such edge return `alternative`.

### See also

[`get_edgeval`](@ref), [`set_edgeval!`](@ref)

### Examples

```jldoctest
julia> gv = ValDiGraph(path_digraph(3), edgeval_types=(a=Float64, b=Int), edgeval_init=(s, d) -> (rand(MersenneTwister(0)), 10))
{3, 2} directed ValDiGraph with
              eltype: Int64
  vertex value types: ()
    edge value types: (a = Float64, b = Int64)
   graph value types: ()

julia> get_edgeval_or(gv, 1, 2, :, missing)
(a = 0.8236475079774124, b = 10)

julia> get_edgeval_or(gv, 1, 3, :, missing)
missing
```
