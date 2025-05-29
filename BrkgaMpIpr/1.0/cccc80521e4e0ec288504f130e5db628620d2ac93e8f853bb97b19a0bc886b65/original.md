```
get_chromosome(brkga_data::BrkgaData, population_index::Int64,
               position::Int64)::Array{Float64, 1}
```

Return a copy of the chromosome ranked at `position` in the population `population_index`. Note that the chromosomes are rakend by fitness and the best chromosome is located in position 1.

# Throws

  * `ErrorException`: if [`initialize!`](@ref) has not been called before.
  * `ArgumentError`: when `population_index < 1` or `population_index > num_independent_populations`.
  * `ArgumentError`: when `position < 1` or `position > population_size`.
