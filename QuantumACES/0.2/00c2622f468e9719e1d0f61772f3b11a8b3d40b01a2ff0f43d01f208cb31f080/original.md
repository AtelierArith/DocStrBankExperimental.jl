```
MemoryData
```

Stim memory simulation results.

# Fields

  * `circuit_param::AbstractCircuitParameters`: Circuit parameters.
  * `noise_param::AbstractNoiseParameters`: Noise parameters.
  * `rounds::Int`: Number of memory circuit rounds.
  * `shots::Int`: Number of sampled shots.
  * `seed::UInt64`: Seed for Stim simulation.
  * `reset_type::Symbol`: Reset type, which is `:meas_reset` by default but can be set to `:meas`.
  * `decoder_type::Symbol`: Decoder type, which is `:pymatching` by default but can be set to `:beliefmatching`.
  * `decoder_gate_probabilities::Vector{Dict{Gate, Vector{Float64}}}`: Vector of gate probabilities used to inform the decoder.
  * `decoder_labels::Vector{String}`: Labels for the gate probabilities in `decoder_gate_probabilities`.
  * `memory_x_observable::Vector{Bool}`: X memory experiment observable across each of the shots.
  * `memory_z_observable::Vector{Bool}`: Z memory experiment observable across each of the shots.
  * `decoder_x_predictions::Matrix{Bool}`: X memory experiment decoder predictions across each of the shots and decoders in `decoder_gate_probabilities`.
  * `decoder_z_predictions::Matrix{Bool}`: Z memory experiment decoder predictions across each of the shots and decoders in `decoder_gate_probabilities`.
