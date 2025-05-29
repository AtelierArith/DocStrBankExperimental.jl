```
simulate_memory(c::AbstractCircuit, rounds::Integer, shots::Integer; kwargs...)
```

Returns the memory and decoding simulation results for a memory experiment conducted with the given syndrome extraction circuit.

WARNING: Seeding has the same features as in Stim. The behaviour of the same random seed will differ across different versions of Stim. Also, when measurement shots are sampled in batches, which occurs when `max_samples` is exceeded, the results will differ from when all shots are sampled at once.

# Arguments

  * `c::AbstractCircuit`: Syndrome extraction circuit.
  * `rounds::Integer`: Number of memory circuit rounds, which must be at least 0.
  * `shots::Integer`: Number of shots, which must be at least 1.

# Keyword arguments

  * `seed::Union{UInt64, Nothing} = nothing`: Seed to use for random number generation.
  * `reset_type::Symbol = :meas_reset`: Reset type, which can be either `:meas_reset` or `:meas`.
  * `decoder_type::Symbol = :pymatching`: Decoder type, which can be either `:pymatching` or `:beliefmatching`.
  * `decoder_gate_probabilities::Vector{Dict{Gate, Vector{Float64}}} = [c.gate_probabilities]`: Gate probabilities used for decoding, the first of which must be the gate probabilities of the supplied circuit `c`.
  * `decoder_labels::Vector{String} = [string(idx) for idx in 1:length(decoder_gate_probabilities)]`: Labels for the decoder gate probabilities.
  * `max_samples::Integer = 10^9`: Maximum number of Stim detector samples collected in a single simulation.
  * `diagnostics::Bool = false`: Whether to print diagnostics.
