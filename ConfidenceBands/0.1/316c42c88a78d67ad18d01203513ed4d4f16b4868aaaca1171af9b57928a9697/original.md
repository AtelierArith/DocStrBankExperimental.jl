```
simulcoverage(lb::AbstractVector, ub::AbstractVector, draws::AbstractMatrix, nuncovered=0)
```

Compute the share of point estimates in bootstrap `draws` that are simultaneously covered by the confidence band with lower bound `lb` and upper bound `ub`, except for at most `nuncovered` parameters. See also [`pwcoverage`](@ref).
