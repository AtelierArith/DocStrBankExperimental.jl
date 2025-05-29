```julia
isVariable(dfg, sym)

```

Return whether `sym::Symbol` represents a variable vertex in the graph DFG. Checks whether it both exists in the graph and is a variable. (If you rather want a quick for type, just do node isa DFGVariable)
