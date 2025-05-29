```
ValGraph{V <: Integer, V_VALS, E_VALS, G_VALS, V_VALS_C, E_VALS_C} <: AbstractValGraph
```

A type representing an undirected simple graph with vertex, edge and graph values.

# Parameters

  * `V`: The type of the vertex indices. Should be a concrete subtype of `Integer`.
  * `V_VALS`: The type of the vertex values, either a `Tuple` or `NamedTuple`.
  * `E_VALS`: The type of the edge values, either a `Tuple` or `NamedTuple`.
  * `G_VALS`: The type of the edge values, either a `Tuple` or `NamedTuple`.
  * `V_VALS_C`: Internal storage parameter, is derived from `V_VALS`
  * `E_VALS_C`: Internal storage parameter, is derived from `E_VALS`

The internal parameters `V_VALS_C` and `E_VALS_C` are automatically calculated by the constructors so that they should usually not be manually specified.
