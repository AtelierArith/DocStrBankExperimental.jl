```julia
lsf(dfg; ...)
lsf(dfg, regexFilter; tags, solvable)

```

List the DFGFactors in the DFG. Optionally specify a label regular expression to retrieves a subset of the factors.

Notes

  * Return `Vector{Symbol}`
