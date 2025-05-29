```
AbstractDIDResult{TR<:AbstractTreatment} <: StatisticalModel
```

Interface supertype for all types that collect estimation results for difference-in-differences with treatment of type `TR`.

# Interface definition

| Required method      | Default definition                             | Brief description                                                                                                     |
|:-------------------- |:---------------------------------------------- |:--------------------------------------------------------------------------------------------------------------------- |
| `coef(r)`            | `r.coef`                                       | Vector of point estimates for all coefficients including covariates                                                   |
| `vcov(r)`            | `r.vcov`                                       | Variance-covariance matrix for estimates in `coef`                                                                    |
| `vce(r)`             | `r.vce`                                        | Covariance estimator                                                                                                  |
| `confint(r)`         | Based on t or normal distribution              | Confidence interval for estimates in `coef`                                                                           |
| `treatment(r)`       | `r.tr`                                         | Treatment specification                                                                                               |
| `nobs(r)`            | `r.nobs`                                       | Number of observations (table rows) involved in estimation                                                            |
| `outcomename(r)`     | `r.yname`                                      | Name of the outcome variable                                                                                          |
| `coefnames(r)`       | `r.coefnames`                                  | Names (`Vector{String}`) of all coefficients including covariates                                                     |
| `treatcells(r)`      | `r.treatcells`                                 | `Tables.jl`-compatible tabular description of treatment coefficients in the order of `coefnames` (without covariates) |
| `weights(r)`         | `r.weights`                                    | Name of the column containing sample weights (if specified)                                                           |
| `ntreatcoef(r)`      | `size(treatcells(r), 1)`                       | Number of treatment coefficients                                                                                      |
| `treatcoef(r)`       | `view(coef(r), 1:ntreatcoef(r))`               | A view of treatment coefficients                                                                                      |
| `treatvcov(r)`       | `(N = ntreatcoef(r); view(vcov(r), 1:N, 1:N))` | A view of variance-covariance matrix for treatment coefficients                                                       |
| `treatnames(r)`      | `coefnames(r)[1:ntreatcoef(r)]`                | Names (`Vector{String}`) of treatment coefficients                                                                    |
| **Optional methods** |                                                |                                                                                                                       |
| `parent(r)`          | `r.parent` or `r`                              | Result object from which `r` is generated                                                                             |
| `dof_residual(r)`    | `r.dof_residual` or `nothing`                  | Residual degrees of freedom                                                                                           |
| `responsename(r)`    | `outcomename(r)`                               | Name of the outcome variable                                                                                          |
| `coefinds(r)`        | `r.coefinds` or `nothing`                      | Lookup table (`Dict{String,Int}`) from `coefnames` to integer indices (for retrieving estimates by name)              |
| `ncovariate(r)`      | `length(coef(r)) - ntreatcoef(r)`              | Number of covariate coefficients                                                                                      |
