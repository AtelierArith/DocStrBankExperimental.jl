```
function flatten_all_chains!(graphs::Union{Tuple,AbstractVector{<:AbstractGraph}}; verbose=0)

Flattens all nodes representing trivial unary chains in-place in the given graphs.
```

# Arguments:

  * `graphs`: A collection of graphs to be processed.
  * `verbose`: Level of verbosity (default: 0).

# Returns:

  * The mutated collection `graphs` with all chains in each graph flattened.
