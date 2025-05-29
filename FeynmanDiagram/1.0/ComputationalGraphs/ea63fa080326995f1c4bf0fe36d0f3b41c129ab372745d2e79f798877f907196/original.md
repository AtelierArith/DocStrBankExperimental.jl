```
function remove_duplicated_leaves!(graphs::Union{Tuple,AbstractVector{<:AbstractGraph}}; verbose=0, normalize=nothing, kwargs...)

Removes duplicated leaf nodes in-place from a collection of graphs. It also provides optional normalization for these leaves.
```

# Arguments:

  * `graphs`: A collection of graphs to be processed.
  * `verbose`: Level of verbosity (default: 0).
  * `normalize`: Optional function to normalize the graphs (default: nothing).
