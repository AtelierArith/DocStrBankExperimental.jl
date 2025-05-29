```julia
lsf(dfg; ...)
lsf(dfg, _)

```

Lists the factors of a specific type in the factor graph.  Example, list all the Point2Point2 factors in the factor graph `dfg`:     lsfWho(dfg, :Point2Point2)

Notes

  * Return `Vector{Symbol}`
