```
get_best_chromosome(brkga_data::BrkgaData)::Array{Float64, 1}
```

Return a copy of the best individual found so far among all populations.

# Throws

  * `ErrorException`: if [`initialize!`](@ref) has not been called before.
