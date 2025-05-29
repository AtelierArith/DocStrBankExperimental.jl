```
independent_set_probabilities([f], reg::YaoAPI.AbstractRegister, graph_or_mis)
```

Calculate the probabilities of independent sets with given postprocessing function `f(config) -> config`. The default postprocessing function `f` will only reduce all configurations to independent set.

# Arguments

  * `f`: optional, postprocessing function, default is [`to_independent_set`](@ref).
  * `reg`: required, the register object.
  * `graph_or_mis`: a problem graph or the MIS size of the problem   graph (can be calculated via [`exact_solve_mis`](@ref)).
