```
exchange_elite!(brkga_data::BrkgaData, num_immigrants::Int64)
```

Exchange elite-solutions between the populations. Given a population, the `num_immigrants` best solutions are copied to the neighbor populations, replacing their worth solutions. If there is only one population, nothing is done.

# Throws

  * `ErrorException`: if [`initialize!`](@ref) has not been called before.
  * `ArgumentError`: when `num_immigrants < 1`.
  * `ArgumentError`: `num_immigrants ≥ ⌈population_size/num_independent_populations⌉ - 1`.
