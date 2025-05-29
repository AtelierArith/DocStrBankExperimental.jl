```
compose_to_file!(concept, name, path; domains, param = nothing, language = :Julia, search = :complete, global_iter = 10, local_iter = 100, metric = hamming, popSize = 200)
```

Explore, learn and compose a function and write it to a file.

# Arguments:

  * `concept`: the concept to learn
  * `name`: the name to give to the constraint
  * `path`: path of the output file

# Keywords arguments:

  * `domains`: domains that defines the search space
  * `param`: an optional parameter of the constraint
  * `language`: the language to export to, default to `:julia`
  * `search`: either `:partial` or `:complete` search
  * `global_iter`: number of learning iteration
  * `local_iter`: number of generation in the genetic algorithm
  * `metric`: the metric to measure the distance between a configuration and known solutions
  * `popSize`: size of the population in the genetic algorithm
