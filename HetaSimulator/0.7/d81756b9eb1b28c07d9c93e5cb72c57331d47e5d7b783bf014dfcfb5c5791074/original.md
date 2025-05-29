```
fit(
  scenario_pairs::AbstractVector{Pair{Symbol, C}},
  parameters_fitted::AbstractVector{<:Pair{Symbol,<:Real}};
  parameters::Union{Nothing, Vector{P}}=nothing,
  alg=DEFAULT_ALG,
  reltol=DEFAULT_FITTING_RELTOL,
  abstol=DEFAULT_FITTING_ABSTOL,
  parallel_type=EnsembleSerial(),
  ftol_abs = 0.0,
  ftol_rel = 1e-4, 
  xtol_rel = 0.0,
  xtol_abs = 0.0, 
  fit_alg = :LN_NELDERMEAD,
  maxeval = 10000,
  maxtime = 0.0,
  lbounds = fill(0.0, length(parameters_fitted)),
  ubounds = fill(Inf, length(parameters_fitted)),
  scale = fill(:lin, length(parameters_fitted)),
  progress::Symbol = :minimal,
  kwargs... 
) where {C<:AbstractScenario, P<:Pair}
```

Fit parameters to experimental measurements. Returns `FitResult` type.

Example: `fit([:x=>scn2, :y=>scn3, :z=>scn4], [:k1=>0.1,:k2=>0.2,:k3=>0.3])`

Arguments:

  * `scenario_pairs` : vector of pairs containing names and scenarios of type [`Scenario`](@ref)
  * `parameters_fitted` : optimization parameters and their initial values
  * `parameters` : parameters, which overwrite both `Model` and `Scenario` parameters. Default is `nothing`
  * `alg` : ODE solver. See SciML docs for details. Default is AutoTsit5(Rosenbrock23())
  * `reltol` : relative tolerance. Default is 1e-6
  * `abstol` : absolute tolerance. Default is 1e-8
  * `parallel_type` : parallel setup. See SciML docs for details. Default is no parallelism: EnsembleSerial()
  * `ftol_abs` : absolute tolerance on function value. See `NLopt.jl` docs for details. Default is `0.0`
  * `ftol_rel` : relative tolerance on function value. See `NLopt.jl` docs for details. Default is `1e-4`
  * `xtol_rel` : relative tolerance on optimization parameters. See `NLopt.jl` docs for details. Default is `0.0`
  * `xtol_abs` : absolute tolerance on optimization parameters. See `NLopt.jl` docs for details. Default is `0.0`
  * `fit_alg` : fitting algorithm. See `NLopt.jl` docs for details. Default is `:LN_NELDERMEAD`
  * `maxeval` : maximum number of function evaluations. See `NLopt.jl` docs for details. Default is `1e4`
  * `maxtime` : maximum optimization time (in seconds). See `NLopt.jl` docs for details. Default is `0`
  * `lbounds` : lower parameters bounds. See `NLopt.jl` docs for details. Default is `fill(0.0, length(parameters_fitted))`
  * `ubounds` : upper parameters bounds. See `NLopt.jl` docs for details. Default is `fill(Inf, length(parameters_fitted))`
  * `scale`   : scale of the parameters (supports `:lin, :direct, :log, :log10`) to be used during fitting. Default is `fill(:lin, length(parameters_fitted))`.             `:direct` value is a synonym of `:lin`.
  * `progress` : progress mode display. One of three values: `:silent`, `:minimal`, `:full`. Default is `:minimal`
  * `kwargs...` : other solver related arguments supported by SciMLBase.solve. See SciML docs for details
