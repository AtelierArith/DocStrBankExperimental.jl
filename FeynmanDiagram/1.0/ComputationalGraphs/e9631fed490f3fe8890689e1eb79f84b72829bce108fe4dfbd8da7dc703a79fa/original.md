```
function merge_multi_product(g::Graph{F,W}) where {F,W}

Returns a copy of computational graph `g` with multiple products merged if they share the same operator (`Prod`).
If `g.operator == Prod`, this function will merge `N` identical subgraphs into a single subgraph with a power operator `Power(N)`. 
The function ensures each unique subgraph is counted and merged appropriately, preserving any distinct subgraph_factors associated with them.
```

# Arguments:

  * `g::Graph`: graph to be modified

# Returns

  * A merged computational graph with potentially fewer subgraphs if there were repeating subgraphs  with the `Prod` operator. If the input graph's operator isn't `Prod`, the function returns the input graph unchanged.
