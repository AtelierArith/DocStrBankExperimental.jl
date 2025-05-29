```julia
isFactor(dfg, sym)

```

Return whether `sym::Symbol` represents a factor vertex in the graph DFG. Checks whether it both exists in the graph and is a factor. (If you rather want a quicker for type, just do node isa DFGFactor)
