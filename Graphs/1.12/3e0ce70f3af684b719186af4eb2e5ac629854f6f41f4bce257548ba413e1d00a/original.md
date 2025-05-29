```
core_periphery_deg(g)
```

Compute the degree-based core-periphery for graph `g`. Return the vertex assignments (`1` for core and `2` for periphery) for each node in `g`.

References:     [Lip](http://arxiv.org/abs/1102.5511))

# Examples

```jldoctest
julia> using Graphs

julia> core_periphery_deg(star_graph(5))
5-element Vector{Int64}:
 1
 2
 2
 2
 2

julia> core_periphery_deg(path_graph(3))
3-element Vector{Int64}:
 2
 1
 2
```
