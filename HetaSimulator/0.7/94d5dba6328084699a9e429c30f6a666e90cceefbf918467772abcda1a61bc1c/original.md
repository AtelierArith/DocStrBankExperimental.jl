```
sim(scenario::Scenario; 
  parameters::AbstractVector{<:Pair{Symbol,<:Real}}=Pair{Symbol, Float64}[],
  alg=DEFAULT_ALG, 
  reltol=DEFAULT_SIMULATION_RELTOL,
  abstol=DEFAULT_SIMULATION_ABSTOL,
  kwargs...)
```

Simulate single `Scenario`. Returns [`SimResult`](@ref) type.

Example: `Scenario(model, (0., 200.); saveat = [0.0, 150.]) |> sim`

Arguments:

  * `scenario` : simulation scenario of type [`Scenario`](@ref)
  * `parameters` : parameters overwrite both `Model` and `Scenario` parameters. Default is empty vector.
  * `alg` : ODE solver. See SciML docs for details. Default is AutoTsit5(Rosenbrock23())
  * `reltol` : relative tolerance. Default is 1e-3
  * `abstol` : relative tolerance. Default is 1e-6
  * `kwargs...` : other solver related arguments supported by SciMLBase.solve. See SciML docs for details
