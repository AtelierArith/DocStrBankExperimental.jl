```
function flatten_chains(g::AbstractGraph) 

Recursively flattens chains of subgraphs within a given graph `g` by merging certain trivial unary subgraphs into their parent graphs,
This function returns a new graph with flatten chains, derived from the input graph `g` remaining unchanged.
```

# Arguments:

  * `g::AbstractGraph`: graph to be modified
