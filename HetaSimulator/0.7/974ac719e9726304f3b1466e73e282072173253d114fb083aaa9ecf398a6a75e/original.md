```
mc(scenario_pairs::Vector{<:AbstractScenario},
  parameters_variation::Vector{<:Pair},
  num_iter::Int64;
  kwargs...
)
```

Run Monte-Carlo simulations with single scenario. Returns `Vector{MCResult}` type.

Example: `mc([scn1,scn2], [:k2=>Normal(1e-3,1e-4), :k3=>Uniform(1e-4,1e-2)], 1000)`

Arguments:

  * `scenario_pairs` : vector of scenarios of type [`Scenario`](@ref)
  * `parameters_variation` : parameters variation setup
  * `num_iter` : number of Monte-Carlo iterations
  * kwargs : other solver related arguments supported by `mc(scenario_pairs::Vector{<:Pair}, parameters_variation::Vector, num_iter::Int64)`
