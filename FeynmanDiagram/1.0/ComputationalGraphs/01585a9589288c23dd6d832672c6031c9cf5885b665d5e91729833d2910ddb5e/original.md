```
function flatten_all_chains!(g::AbstractGraph; verbose=0)
```

F     Flattens all nodes representing trivial unary chains in-place in the given graph `g`. 

# Arguments:

  * `graphs`: The graph to be processed.
  * `verbose`: Level of verbosity (default: 0).

# Returns:

  * The mutated graph `g` with all chains flattened.
