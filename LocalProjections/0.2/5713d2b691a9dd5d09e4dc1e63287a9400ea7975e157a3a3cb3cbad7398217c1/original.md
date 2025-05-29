```
lp([estimator], data, ynames; kwargs...)
```

Estimate local projections with the specified `estimator` for outcome variable(s) with column name(s) `ynames` in `data` table. If the `estimator` is not specified, [`LeastSquaresLP`](@ref) is assumed. The input `data` must be `Tables.jl`-compatible.

# Keywords

  * `xnames=()`: indices of contemporaneous regressors from `data`.
  * `wnames=()`: indices of lagged control variables from `data`.
  * `nlag::Int=4`: number of lags to be included for the lagged control variables.
  * `nhorz::Int=1`: total number of horizons to be estimated.
  * `minhorz::Int=0`: the minimum horizon involved in estimation.
  * `normalize::Union{VarIndexPair,Vector{VarIndexPair},Nothing}=nothing`: normalize the magnitude of the specified regressor(s) based on their initial impact on the respective targeted outcome variable.
  * `iv::Union{Pair,Nothing}=nothing`: endogenous varable(s) paired with instrument(s).
  * `firststagebyhorz::Bool=false`: estimate the first-stage regression separately for each horizon.
  * `testweakiv::Bool=true`: compute Kleibergen-Paap rk statistic for weak IV.
  * `states=nothing`: variable(s) representing the states for a state-dependent specification.
  * `panelid::Union{Symbol,Integer,Nothing}=nothing`: variable identifying the units in a panel.
  * `fes=()`: variable(s) identifying the fixed effects.
  * `addpanelidfe::Bool=true`: use `panelid` for unit fixed effects.
  * `panelweight::Union{Symbol,Integer,Nothing}=nothing`: weights across units in a panel.
  * `vce::CovarianceEstimator=HRVCE()`: the variance-covariance estimator.
  * `subset::Union{BitVector,Nothing}=nothing`: subset of `data` to be used for estimation.
  * `addylag::Bool=true`: include lags of the outcome variable(s).
  * `nocons::Bool=false`: do not add the constant term.
  * `TF::Type=Float64`: numeric type used for estimation.
