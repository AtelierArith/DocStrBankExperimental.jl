```
pwcoverage(lb::AbstractVector, ub::AbstractVector, draws::AbstractMatrix)
```

Compute the share of point estimates in bootstrap `draws` that are covered by the corresponding confidence intervals with lower bounds `lb` and upper bounds `ub` for each parameter separately. See also [`simulcoverage`](@ref).
