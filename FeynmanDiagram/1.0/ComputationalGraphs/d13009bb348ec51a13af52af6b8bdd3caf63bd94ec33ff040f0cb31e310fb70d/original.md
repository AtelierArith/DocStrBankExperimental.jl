```
function remove_zero_valued_subgraphs!(g::AbstractGraph)

Removes zero-valued (zero subgraph_factor) subgraph(s) of a computational graph `g`. If all subgraphs are zero-valued, the first one (`eldest(g)`) will be retained.
```

# Arguments:

  * `g::AbstractGraph`: graph to be modified
