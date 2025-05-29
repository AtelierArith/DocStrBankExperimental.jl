```
mc!(mcres::M; 
  success_status::Vector{Symbol}=[:Success,:Terminated]
  kwargs...
) where M <: Union{MCResult, Vector{MCResult}, Vector{Pair}}
```

Re-run failed Monte-Carlo simulations with single `Scenario`. Updates `MCResult` type.

Example: `mc!(mcres)`

Arguments:

  * `mcres` : Monte-Carlo result of type `MCResult`
  * `success_status` : Vector of success statuses. Default is `[:Success,:Terminated]`
  * kwargs : other solver related arguments supported by `mc(scenario::Scenario, parameters_variation::Vector, num_iter::Int64)`
