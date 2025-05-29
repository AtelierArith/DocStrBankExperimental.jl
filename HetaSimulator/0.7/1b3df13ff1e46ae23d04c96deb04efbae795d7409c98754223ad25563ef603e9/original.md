```
mc(scenario_pairs::Vector{<:Pair},
  parameters_variation::Vector{<:Pair},
  num_iter::Int64;
  verbose=false,
  alg=DEFAULT_ALG,
  reltol=DEFAULT_SIMULATION_RELTOL,
  abstol=DEFAULT_SIMULATION_ABSTOL,
  parallel_type=EnsembleSerial(),
  kwargs...
)
```

Run Monte-Carlo simulations with single `Scenario`. Returns `Vector{MCResult}` type.

Example: `mc([:c1=>scn1,:c2=>scn2], [:k2=>Normal(1e-3,1e-4), :k3=>Uniform(1e-4,1e-2)], 1000)`

Arguments:

  * `scenario_pairs` : vector of pairs containing names and scenarios of type [`Scenario`](@ref)
  * `parameters_variation` : parameters variation setup
  * `num_iter` : number of Monte-Carlo iterations
  * `verbose` : print iteration progress. Default is `false`
  * `progress_bar` : show progress bar. Default is `false`
  * `alg` : ODE solver. See SciML docs for details. Default is AutoTsit5(Rosenbrock23())
  * `reltol` : relative tolerance. Default is 1e-3
  * `abstol` : relative tolerance. Default is 1e-6
  * `output_func` : the function determines what is saved from the solution to the output array. Defaults to saving the solution itself
  * `reduction_func` : this function determines how to reduce the data in each batch. Defaults to appending the data from the batches
  * `parallel_type` : parallel setup. See SciML docs for details. Default is no parallelism: EnsembleSerial()
  * kwargs : other solver related arguments supported by SciMLBase.solve. See SciML docs for details
