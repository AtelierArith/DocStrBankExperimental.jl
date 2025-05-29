```
ACESData
```

ACES noise characterisation experiment simulation results.

# Fields

  * `d::Design`: Experimental design.
  * `noise_est_coll::Matrix{NoiseEstimate}`: Noise estimates for each repetition and measurement budget.
  * `noise_error_coll::Matrix{NoiseError}`: Noise errors for each repetition and measurement budget.
  * `budget_set::Vector{Int}`: Measurement budgets.
  * `shots_set::Vector{Int}`: Measurement shots corresponding to the measurement budgets in `budget_set`.
  * `repetitions::Int`: Repetitions of simulating an ACES noise characterisation experiment.
  * `seed::UInt64`: Seed used to generate the random seeds for each repetition.
  * `seeds::Vector{UInt64}`: Seeds for each of the repetitions.
  * `calculation_times::Matrix{Float64}`: Time taken to simulate sampling, and to estimate the gate eigenvalues and project them into the probability simplex, for each repetition.
  * `overall_time::Float64`: Overall time taken to simulate ACES across all repetitions.
