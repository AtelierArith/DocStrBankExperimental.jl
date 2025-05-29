```julia
listVariables(dfg; ...)
listVariables(dfg, regexFilter; tags, solvable)

```

Get a list of labels of the DFGVariables in the graph. Optionally specify a label regular expression to retrieves a subset of the variables. Tags is a list of any tags that a node must have (at least one match).

Notes

  * Returns `::Vector{Symbol}`

Example

```julia
listVariables(dfg, r"l", tags=[:APRILTAG;])
```

See also: [`ls`](@ref)
