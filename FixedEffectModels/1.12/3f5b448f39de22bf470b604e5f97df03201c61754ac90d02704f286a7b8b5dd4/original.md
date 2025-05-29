Estimate a linear model with high dimensional categorical variables / instrumental variables

### Arguments

  * `df`: a Table
  * `FormulaTerm`: A formula created using [`@formula`](@ref)
  * `CovarianceEstimator`: A method to compute the variance-covariance matrix

### Keyword arguments

  * `contrasts::Dict = Dict()` An optional Dict of contrast codings for each categorical variable in the `formula`.  Any unspecified variables will have `DummyCoding`.
  * `weights::Union{Nothing, Symbol}` A symbol to refer to a columns for weights
  * `save::Symbol`: Should residuals and eventual estimated fixed effects saved in a dataframe? Default to `:none` Use `save = :residuals` to only save residuals, `save = :fe` to only save fixed effects, `save = :all` for both. Once saved, they can then be accessed using `residuals(m)` or `fe(m)` where `m` is the object returned by the estimation. The returned DataFrame is automatically aligned with the original DataFrame.
  * `method::Symbol`: A symbol for the method. Default is :cpu. Alternatively,  use :CUDA or :Metal  (in this case, you need to import the respective package before importing FixedEffectModels)
  * `nthreads::Integer` Number of threads to use in the estimation. If `method = :cpu`, defaults to `Threads.nthreads()`. Otherwise, defaults to 256.
  * `double_precision::Bool`: Should the demeaning operation use Float64 rather than Float32? Default to true if `method =:cpu' and false if`method = :CUDA`or`method = :Metal`.
  * `tol::Real` Tolerance. Default to 1e-6.
  * `maxiter::Integer = 10000`: Maximum number of iterations
  * `drop_singletons::Bool = true`: Should singletons be dropped?
  * `progress_bar::Bool = true`: Should the regression show a progressbar?
  * `first_stage::Bool = true`: Should the first-stage F-stat and p-value be computed?
  * `subset::Union{Nothing, AbstractVector} = nothing`: select specific rows.

### Details

Models with instruments variables are estimated using 2SLS. `reg` tests for weak instruments by computing the Kleibergen-Paap rk Wald F statistic, a generalization of the Cragg-Donald Wald F statistic for non i.i.d. errors. The statistic is similar to the one returned by the Stata command `ivreg2`.

### Examples

```julia
using RDatasets, FixedEffectModels
df = dataset("plm", "Cigar")
reg(df, @formula(Sales ~ NDI + fe(State) + fe(State)&Year))
reg(df, @formula(Sales ~ NDI + fe(State)*Year))
reg(df, @formula(Sales ~ (Price ~ Pimin)))
reg(df, @formula(Sales ~ NDI), Vcov.robust())
reg(df, @formula(Sales ~ NDI), Vcov.cluster(:State))
reg(df, @formula(Sales ~ NDI), Vcov.cluster(:State , :Year))
df.YearC = categorical(df.Year)
reg(df, @formula(Sales ~ YearC), contrasts = Dict(:YearC => DummyCoding(base = 80)))
```

### Alias

`reg` is an alias for the more typical StatsAPI `fit`

```julia
using RDatasets, FixedEffectModels
df = dataset("plm", "Cigar")
fit(FixedEffectModel, @formula(Sales ~ NDI + fe(State) + fe(State)&Year), df)
```
