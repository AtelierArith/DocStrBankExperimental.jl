```julia
deleteVariable!(dfg, variable)

```

Delete a referenced DFGVariable from the DFG.

Notes

  * Returns `Tuple{AbstractDFGVariable, Vector{<:AbstractDFGFactor}}`
