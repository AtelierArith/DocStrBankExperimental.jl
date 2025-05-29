```
get_best_fitness!(brkga_data::BrkgaData)::Float64
```

Return the fitness/value of the best individual found so far among all populations.

# Throws

  * `ErrorException`: if [`initialize!`](@ref) has not been called before.
