```
exogenous_outputs(sys, idxs::Union{Int, Vector{Int}})
```

Get the exogenous output connectors in `sys` at indices `idxs`.

If `idxs` is a single integer, the output will be the connector, if it is a vector of integers, the output will be a vecotr of connectors.
