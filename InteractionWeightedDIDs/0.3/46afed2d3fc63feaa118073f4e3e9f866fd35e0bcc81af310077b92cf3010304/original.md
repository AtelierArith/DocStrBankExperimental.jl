```
agg(r::RegressionBasedDIDResult{<:DynamicTreatment}, names=nothing; kwargs...)
```

Aggregate coefficient estimates from `r` by values taken by the columns from `r.treatcells` indexed by `names` with weights proportional to `treatweights` within each relative time.

# Keywords

  * `bys=nothing`: columnwise transformations over `r.treatcells` before grouping by `names`.
  * `subset=nothing`: subset of treatment coefficients used for aggregation.
