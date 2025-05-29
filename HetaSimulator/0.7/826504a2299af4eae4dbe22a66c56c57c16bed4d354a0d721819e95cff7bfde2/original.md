```
mc(scenario::Scenario,
  parameters_variation::DataFrame,
  num_iter::Int;
  kwargs...
)
```

Run Monte-Carlo simulations with single scenario `Scenario`. Returns [`MCResult`](@ref) type.

Example: `mc(scn1, DataFrame(k2=rand(3),k3=rand(3)), 1000)`

Arguments:

  * `scenario` : simulation scenario of type [`Scenario`](@ref)
  * `parameters_variation` : DataFrame with pre-generated parameters.
  * `num_iter` : number of Monte-Carlo iterations
  * kwargs : other solver related arguments supported by `mc(scenario::Scenario, parameters_variation::Vector, num_iter::Int64)`
