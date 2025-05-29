```
function optimize(graphs::Union{Tuple,AbstractVector{<:AbstractGraph}}; level=0, verbose=0, normalize=nothing)

Optimizes a copy of given `graphs`. Removes duplicated nodes (when `level > 0`) or leaves, flattens chains, 
merges linear combinations, and removing zero-valued subgraphs.
```

# Arguments:

  * `graphs`: A tuple or vector of graphs.
  * `level`: Optimization level (default: 0). A value greater than 0 triggers more extensive but slower optimization processes, such as removing duplicated nodes.
  * `verbose`: Level of verbosity (default: 0).
  * `normalize`: Optional function to normalize the graphs (default: nothing).

# Returns:

  * A tuple/vector of optimized graphs.
