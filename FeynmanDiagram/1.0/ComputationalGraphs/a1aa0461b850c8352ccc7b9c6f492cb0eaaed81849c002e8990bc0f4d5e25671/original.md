```
function remove_zero_valued_subgraphs(g::AbstractGraph)

Returns a copy of graph `g` with zero-valued (zero subgraph_factor) subgraph(s) removed.
If all subgraphs are zero-valued, the first one (`eldest(g)`) will be retained.
```

# Arguments:

  * `g::AbstractGraph`: graph to be modified
