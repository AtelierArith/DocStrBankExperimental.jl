```julia
getVariable(dfg, label, solveKey)

```

Get a DFGVariable with a specific solver key. In memory types still return a reference, other types returns a variable with only solveKey.
