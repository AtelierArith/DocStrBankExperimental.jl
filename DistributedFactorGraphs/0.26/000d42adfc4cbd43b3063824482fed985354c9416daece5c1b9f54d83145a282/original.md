```julia
deleteVariable!(dfg, variable)

```

Delete a referenced VariableCompute from the DFG.

Notes

  * Returns `Tuple{AbstractDFGVariable, Vector{<:AbstractDFGFactor}}`
