```
RegressionBasedDID <: DiffinDiffsEstimator
```

Estimation procedure for regression-based difference-in-differences.

A `StatsSpec` for this procedure accepts the following arguments:

| Key                | Type restriction                            | Default value              | Description                                                                                      |
|:------------------ |:------------------------------------------- |:-------------------------- |:------------------------------------------------------------------------------------------------ |
| `data`             |                                             |                            | A `Tables.jl`-compatible data table                                                              |
| `tr`               | `DynamicTreatment{SharpDesign}`             |                            | Treatment specification                                                                          |
| `pr`               | `TrendOrUnspecifiedPR{Unconditional,Exact}` |                            | Parallel trend assumption                                                                        |
| `yterm`            | `AbstractTerm`                              |                            | A term for outcome variable                                                                      |
| `treatname`        | `Symbol`                                    |                            | Column name for the variable representing treatment time                                         |
| `subset`           | `Union{BitVector,Nothing}`                  | `nothing`                  | Rows from `data` to be used for estimation                                                       |
| `weightname`       | `Union{Symbol,Nothing}`                     | `nothing`                  | Column name of the sample weight variable                                                        |
| `vce`              | `Vcov.CovarianceEstimator`                  | `Vcov.CovarianceEstimator` | Variance-covariance estimator                                                                    |
| `treatintterms`    | `TermSet`                                   | `TermSet()`                | Terms interacted with the treatment indicators                                                   |
| `xterms`           | `TermSet`                                   | `TermSet()`                | Terms for covariates and fixed effects                                                           |
| `contrasts`        | `Union{Dict{Symbol,Any},Nothing}`           | `nothing`                  | Contrast coding to be processed by `StatsModels.jl`                                              |
| `drop_singletons`  | `Bool`                                      | `true`                     | Drop singleton observations for fixed effects                                                    |
| `nfethreads`       | `Int`                                       | `Threads.nthreads()`       | Number of threads to be used for solving fixed effects                                           |
| `fetol`            | `Float64`                                   | `1e-8`                     | Tolerance level for the fixed effect solver                                                      |
| `femaxiter`        | `Int`                                       | `10000`                    | Maximum number of iterations allowed for the fixed effect solver                                 |
| `cohortinteracted` | `Bool`                                      | `true`                     | Interact treatment indicators by treatment time                                                  |
| `solvelsweights`   | `Bool`                                      | `false`                    | Solve the cell-level least-square weights with default cell partition                            |
| `lswtnames`        | Iterable of `Symbol`s                       | `tuple()`                  | Column names from `treatcells` defining the cell partition used for solving least-square weights |
