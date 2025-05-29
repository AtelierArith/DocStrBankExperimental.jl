```
walk_tree!(g, labels, ex, show_call=true)
```

Walk the abstract syntax tree (AST) of the given expression `ex`. Builds up the graph `g` and the set of `labels` for each node, both modified in place

`show_call` specifies whether to include `call` nodes in the graph. Including them represents the Julia AST more precisely, but adds visual noise.

Returns the number of the top vertex.
