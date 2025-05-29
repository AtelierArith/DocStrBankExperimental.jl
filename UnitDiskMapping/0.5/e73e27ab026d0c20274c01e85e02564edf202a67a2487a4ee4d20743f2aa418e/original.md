```
map_graph([mode=UnWeighted(),] g::SimpleGraph; vertex_order=MinhThiTrick(), ruleset=[...])
```

Map a graph to a unit disk grid graph that being "equivalent" to the original graph, and return a `MappingResult` instance. Here "equivalent" means a maximum independent set in the grid graph can be mapped back to a maximum independent set of the original graph in polynomial time.

## Positional Arguments

  * `mode` is optional, it can be `Weighted()` (default) or `UnWeighted()`.
  * `g` is a graph instance, check the documentation of [`Graphs`](https://juliagraphs.org/Graphs.jl/dev/) for details.

## Keyword Arguments

  * `vertex_order` specifies the order finding algorithm for vertices.

Different vertex orders have different path width, i.e. different depth of mapped grid graph. It can be a vector or one of the following inputs     * `Greedy()` fast but not optimal.     * `MinhThiTrick()` slow but optimal.

  * `ruleset` specifies and extra set of optimization patterns (not the crossing patterns).
