```
MemorySummary
```

Stim memory simulation summary results.

# Fields

  * `circuit_param::AbstractCircuitParameters`: Circuit parameters.
  * `noise_param::AbstractNoiseParameters`: Noise parameters.
  * `rounds::Int`: Number of memory circuit rounds.
  * `shots::Int`: Number of sampled shots.
  * `seed::UInt64`: Seed for Stim simulation.
  * `reset_type::Symbol`: Reset type, which is `:meas_reset` by default but can be set to `:meas`.
  * `decoder_type::Symbol`: Decoder type, which is `:pymatching` by default but can be set to `:beliefmatching`.
  * `decoder_labels::Vector{String}`: Labels for the decoder gate probabilities.
  * `memory_x_errors::Vector{Float64}`: X memory experiment error rate.
  * `memory_z_errors::Vector{Float64}`: Z memory experiment error rate.
  * `memory_x_errors_cov::Matrix{Float64}`: X memory experiment error rate covariance.
  * `memory_z_errors_cov::Matrix{Float64}`: Z memory experiment error rate covariance.
  * `change_x_errors::Matrix{Float64}`: X memory experiment change in error rate across different gate probabilities.
  * `change_z_errors::Matrix{Float64}`: Z memory experiment change in error rate across different gate probabilities.
  * `change_x_errors_sem::Matrix{Float64}`: X memory experiment change in error rate across different gate probabilities standard error of the mean.
  * `change_z_errors_sem::Matrix{Float64}`: Z memory experiment change in error rate across different gate probabilities standard error of the mean.
  * `decoder_x_confusion::Matrix{Int}`: X memory experiment decoder confusion matrix.
  * `decoder_z_confusion::Matrix{Int}`: Z memory experiment decoder confusion matrix.
