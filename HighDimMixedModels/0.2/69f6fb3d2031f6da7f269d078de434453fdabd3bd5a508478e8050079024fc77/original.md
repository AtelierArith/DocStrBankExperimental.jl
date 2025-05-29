```
coeftable(fit::HDMModel, names::Vector{String}=string.(1:length(fit.fixef)))
```

Return a table of the *selected* coefficients, i.e. those not set to 0, from the model.

# Arguments

  * `fit::HDMModel`: A fitted model.
  * `names::Vector{String}`: Names of the all the coefficients in the model (not just those selected), defaults to integer names

# Returns

A `StatsBase.CoefTable` object.
