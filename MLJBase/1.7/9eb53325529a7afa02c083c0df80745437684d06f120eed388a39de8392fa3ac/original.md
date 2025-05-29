```
origins(N)
```

Return a list of all origins of a node `N` accessed by a call `N()`. These are the source nodes of ancestor graph of `N` if edges corresponding to training arguments are excluded. A `Node` object cannot be called on new data unless it has a unique origin.

Not to be confused with `sources(N)` which refers to the same graph but without the training edge deletions.

See also: [`node`](@ref), [`source`](@ref).
