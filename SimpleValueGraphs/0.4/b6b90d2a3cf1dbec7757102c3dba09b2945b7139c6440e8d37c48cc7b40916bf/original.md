```
ValOutDiGraph{V, V_VALS, E_VALS}(
    g::SimpleDiGraph;
    vertexval_init,
    edgeval_init,
    graphvals=()
)
ValOutDiGraph{V = eltype(g)}(
    g::SimpleDiGraph;
    vertexval_types=(),
    edgeval_types=(),
    vertexval_init,
    edgeval_init,
    graphvals=()
)
```

Construct a `ValOutDiGraph` with the same structure as `g`.

# Arguments

  * `g`: A `Graphs.SimpleDiGraph`

# Keywords

  * `vertexval_init`: How the vertex values of this graph should be initialized.   Can be either a function `v -> (values...)` or `undef`. Can be omitted if this   graph has no vertex values.
  * `edgeval_init`: How the edge values of this graph should be initialized.   Can be either a function `(s,d) -> (values...)` or `undef`. Can be omitted if this   graph has no edge values.
  * `vertexval_types`: A `Tuple` or `NamedTuple` of types.
  * `edgeval_types`: A `Tuple` or `NamedTuple` of types.
  * `grapvals`: A `Tuple` or `NamedTuple` of graph values.

# Parameters

  * `V` the eltype of this graphs vertices. `eltype(g) if omitted.
  * `V_VALS` The type (either a `Tuple` or a `NamedTuple` type) of vertex values. Can   alternatively be specified with the `vertexval_init` keyword argument.
  * `E_VALS` The type (either a `Tuple` or a `NamedTuple` type) of edge values. Can   alternatively be specified with the `edgeval_init` keyword argument.
