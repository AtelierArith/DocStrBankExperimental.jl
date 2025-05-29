```
get_current_population(brkga_data::BrkgaData,
                       population_index::Int64)::Population
```

Return a reference for population `population_index`.

!!! note
    This function is implemented for complaince with the C++ API. The user can access the population directly using `brkga_data.current[population_index]`.


!!! warning
    IT IS NOT ADIVISED TO CHANGE THE POPULATION DIRECTLY, since such changes can result in undefined behavior.


# Throws

  * `ErrorException`: if [`initialize!`](@ref) has not been called before.
  * `ArgumentError`: when `population_index < 1` or `population_index > num_independent_populations`.
