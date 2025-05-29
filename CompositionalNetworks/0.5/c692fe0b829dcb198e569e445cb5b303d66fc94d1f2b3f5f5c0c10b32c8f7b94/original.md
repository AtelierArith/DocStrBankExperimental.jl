```
explore_learn_compose(concept; domains, param = nothing, search = :complete, global_iter = 10, local_iter = 100, metric = hamming, popSize = 200, action = :composition)
```

Explore a search space, learn a composition from an ICN, and compose an error function.

# Arguments:

  * `concept`: the concept of the targeted constraint
  * `domains`: domains of the variables that define the training space
  * `param`: an optional parameter of the constraint
  * `search`: either `flexible`,`:partial` or `:complete` search. Flexible search will use `search_limit` and `solutions_limit` to determine if the search space needs to be partially or completely explored
  * `global_iter`: number of learning iteration
  * `local_iter`: number of generation in the genetic algorithm
  * `metric`: the metric to measure the distance between a configuration and known solutions
  * `popSize`: size of the population in the genetic algorithm
  * `action`: either `:symbols` to have a description of the composition or `:composition` to have the composed function itself
