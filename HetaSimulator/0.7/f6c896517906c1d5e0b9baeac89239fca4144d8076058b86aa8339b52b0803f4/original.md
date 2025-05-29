```
sim(scenario_pairs::Vector{P}; 
  parameters::AbstractVector{<:Pair{Symbol, <:Real}}=Pair{Symbol, Float64}[],
  alg=DEFAULT_ALG, 
  reltol=DEFAULT_SIMULATION_RELTOL, 
  abstol=DEFAULT_SIMULATION_ABSTOL,
  parallel_type=EnsembleSerial(),
  kwargs...) where P<:Pair
```

Simulate multiple scenarios. Returns `Vector{Pair}`.

Example: `sim([:x => scn1, :y=>scn2, :z=>scn3])`

Arguments:

  * `scenario_pairs` : vector of pairs containing names and scenarios of type [`Scenario`](@ref)
  * `parameters` : parameters, which overwrite both `Model` and `Scenario` parameters. Default is empty vector.
  * `alg` : ODE solver. See SciML docs for details. Default is AutoTsit5(Rosenbrock23())
  * `reltol` : relative tolerance. Default is 1e-3
  * `abstol` : relative tolerance. Default is 1e-6
  * `parallel_type` : type of multiple simulations parallelism. Default is no parallelism. See SciML docs for details
  * `kwargs...` : other solver related arguments supported by SciMLBase.solve. See SciML docs for de     #update*init*values(scn*i.prob, scn*i.init*func, parameters*nt) tails
