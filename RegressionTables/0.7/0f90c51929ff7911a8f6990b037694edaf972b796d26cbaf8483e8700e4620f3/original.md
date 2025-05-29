Produces a publication-quality regression table, similar to Stata's `esttab` and R's `stargazer`.

### Arguments

  * `rr::FixedEffectModel...` are the `FixedEffectModel`s from `FixedEffectModels.jl` that should be printed. Only required argument.
  * `keep` is a `Vector` of regressor names (`String`s), integers, ranges or regex that should be shown, in that order. Defaults to an empty vector, in which case all regressors will be shown. The strings should be the relabeld names of the coefficients.
  * `drop` is a `Vector` of regressor names (`String`s), integers, ranges or regex that should not be shown. Defaults to an empty vector, in which case no regressors will be dropped. The strings should be the relabeld names of the coefficients.
  * `order` is a `Vector` of regressor names (`String`s), integers, ranges or regex that should be shown in that order. Defaults to an empty vector, in which case the order of regressors will be unchanged. Other regressors are still shown (assuming `drop` is empty). The strings should be the relabeld names of the coefficients.
  * `fixedeffects` is a `Vector` of FE names (`String`s), integers, ranges or regex that should be shown, in that order. Defaults to an empty vector, in which case all FE's will be shown.
  * `align` is a `Symbol` from the set `[:l,:c,:r]` indicating the alignment of results columns (default `:r` right-aligned). Currently works only with ASCII and LaTeX output.
  * `header_align` is a `Symbol` from the set `[:l,:c,:r]` indicating the alignment of the header row (default `:c` centered). Currently works only with ASCII and LaTeX output.
  * `labels` is a `Dict` that contains displayed labels for variables (`String`s) and other text in the table. If no label for a variable is found, it default to variable names. See documentation for special values.
  * `estimformat` is a `String` that describes the format of the estimate.
  * `digits` is an `Int` that describes the precision to be shown in the estimate. Defaults to `nothing`, which means the default (3) is used (default can be changed by setting `RegressionTables.default_digits(render::AbstractRenderType, x) = 3`).
  * `statisticformat` is a `String` that describes the format of the number below the estimate (se/t).
  * `digits_stats` is an `Int` that describes the precision to be shown in the statistics. Defaults to `nothing`, which means the default (3) is used (default can be changed by setting `RegressionTables.default_digits(render::AbstractRenderType, x) = 3`).
  * `below_statistic` is a type that describes a statistic that should be shown below each point estimate. Recognized values are `nothing`, `StdError`, `TStat`, and `ConfInt`. `nothing` suppresses the line. Defaults to `StdError`.
  * `regression_statistics` is a `Vector` of types that describe statistics to be shown at the bottom of the table. Built in recognized types are `Nobs`, `R2`, `PseudoR2`, `R2CoxSnell`, `R2Nagelkerke`, `R2Deviance`, `AdjR2`, `AdjPseudoR2`, `AdjR2Deviance`, `DOF`, `LogLikelihood`, `AIC`, `AICC`, `BIC`, `FStat`, `FStatPValue`, `FStatIV`, `FStatIVPValue`, R2Within. Defaults vary based on regression inputs (simple linear model is [Nobs, R2]).
  * `extralines` is a `Vector` or a `Vector{<:AbsractVector}` that will be added to the end of the table. A single vector will be its own row, a vector of vectors will each be a row. Defaults to `nothing`.
  * `number_regressions` is a `Bool` that governs whether regressions should be numbered. Defaults to `true`.
  * `groups` is a `Vector`, `Vector{<:AbstractVector}` or `Matrix` of labels used to group regressions. This can be useful if results are shown for different data sets or sample restrictions.
  * `print_fe_section` is a `Bool` that governs whether a section on fixed effects should be shown. Defaults to `true`.
  * `print_estimator_section`  is a `Bool` that governs whether to print a section on which estimator (OLS/IV/Binomial/Poisson...) is used. Defaults to `true` if more than one value is displayed.
  * `standardize_coef` is a `Bool` that governs whether the table should show standardized coefficients. Note that this only works with `TableRegressionModel`s, and that only coefficient estimates and the `below_statistic` are being standardized (i.e. the R^2 etc still pertain to the non-standardized regression).
  * `render::AbstractRenderType` is a `AbstractRenderType` type that governs how the table should be rendered. Standard supported types are ASCII (via `AsciiTable()`) and LaTeX (via `LatexTable()`). Defaults to `AsciiTable()`.
  * `file` is a `String` that governs whether the table should be saved to a file. Defaults to `nothing`.
  * `transform_labels` is a `Dict` or one of the `Symbol`s `:ampersand`, `:underscore`, `:underscore2space`, `:latex`
  * `confint_level` is a `Float64` that governs the confidence level for the confidence interval. Defaults to `0.95`.

### Details

A typical use is to pass a number of `FixedEffectModel`s to the function, along with how it should be rendered (with `render` argument):

```julia
regtable(regressionResult1, regressionResult2; render = AsciiTable())
```

Pass a string to the `file` argument to create or overwrite a file. For example, using LaTeX output,

```julia
regtable(regressionResult1, regressionResult2; render = LatexTable(), file="myoutfile.tex")
```

See the full argument list for details.
