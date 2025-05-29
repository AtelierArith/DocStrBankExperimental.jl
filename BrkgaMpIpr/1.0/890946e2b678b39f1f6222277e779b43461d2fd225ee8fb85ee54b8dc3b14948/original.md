```
function shake!(brkga_data::BrkgaData, intensity::Int64,
                shaking_type::ShakingType, population_index::Int64 = Inf64)
```

Perform a shaking in the chosen population. The procedure applies changes (shaking) on elite chromosomes and fully reset the remaining population.

# Arguments

  * `intensity::Int64`: the intensity of the shaking (> 0);
  * [`shaking_type::ShakingType`](@ref ShakingType): either `CHANGE` or `SWAP` moves;
  * `population_index::Int64`: the index of the population to be shaken. If `population_index > num_independent_populations`, all populations are shaken.

# Throws

  * `ErrorException`: if [`initialize!`](@ref) has not been called before.
  * `ArgumentError`: when `population_index < 1` or `intensity < 1`.
