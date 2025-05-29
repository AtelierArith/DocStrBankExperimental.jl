```
function inject_chromosome!(brkga_data::BrkgaData,
                            chromosome::Array{Float64, 1},
                            population_index::Int64,
                            position::Int64,
                            fitness::Float64 = Inf)
```

Inject `chromosome` and its `fitness` into population `population_index` in the `position` place. If fitness is not provided (`fitness = Inf`), the decoding is performed over `chromosome`. Once the chromosome is injected, the population is re-sorted according to the chromosomes' fitness.

# Throws

  * `ErrorException`: if [`initialize!`](@ref) has not been called before.
  * `ArgumentError`: when `population_index < 1` or `population_index > num_independent_populations`.
  * `ArgumentError`: when `position < 1` or `position > population_size`.
  * `ArgumentError`: when `lenght(chromosome) != chromosome_size`.
