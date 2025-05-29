```
function optimize!(graphs::Union{Tuple,AbstractVector{<:AbstractGraph}}; level=0, verbose=0, normalize=nothing)

In-place optimization of given `graphs`. Removes duplicated leaves, flattens chains, 
merges linear combinations, and removes zero-valued subgraphs. When `level > 0`, also removes duplicated intermediate nodes.
```

# Arguments:

  * `graphs`: A tuple or vector of graphs.
  * `level`: Optimization level (default: 0). A value greater than 0 triggers more extensive but slower optimization processes, such as removing duplicated intermediate nodes.
  * `verbose`: Level of verbosity (default: 0).
  * `normalize`: Optional function to normalize the graphs (default: nothing).

# Returns

  * Returns the optimized graphs. If the input graphs is empty, it returns nothing.
