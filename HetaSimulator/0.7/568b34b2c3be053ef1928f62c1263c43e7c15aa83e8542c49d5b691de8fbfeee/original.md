```
function estimator(
  scenario_pairs::AbstractVector{Pair{Symbol, C}},
  parameters_fitted::AbstractVector{<:Pair{Symbol,<:Real}};
  parameters::Union{Nothing, Vector{P}}=nothing,
  alg=DEFAULT_ALG,
  reltol=DEFAULT_FITTING_RELTOL,
  abstol=DEFAULT_FITTING_ABSTOL,
  parallel_type=EnsembleSerial(),
  kwargs... # other arguments to sim
) where {C<:AbstractScenario, P<:Pair}
```

Generates likelihood estimator function for parameter identification and analysis.   It corresponds to `-2ln(L)` as a function depending on parameter set.

Example: `estimator([:x=>scn2, :y=>scn3, :z=>scn4], [:k1=>0.1,:k2=>0.2,:k3=>0.3])`

Arguments:

  * `scenario_pairs` : vector of pairs containing names and scenarios of type [`Scenario`](@ref)
  * `parameters_fitted` : parameters and their nominal values that will be used as default
  * `parameters` : paramters, which overwrite both `Model` and `Scenario` parameters. Default is `nothing`
  * `alg` : ODE solver. See SciML docs for details. Default is AutoTsit5(Rosenbrock23())
  * `reltol` : relative tolerance. Default is 1e-6
  * `abstol` : relative tolerance. Default is 1e-8
  * `parallel_type` : parallel setup. See SciML docs for details. Default is no parallelism: EnsembleSerial()
  * `kwargs...` : other ODE solver related arguments supported by `SciMLBase.solve`. See SciML docs for details

Returns:

```
function(x:Vector{Float64}=last.(parameters_fitted))
```

The method returns anonimous function which depends on parameters vector in the same order as in `parameters_fitted`.   This function is ready to be passed to optimizer routine or identifiability analysis.
