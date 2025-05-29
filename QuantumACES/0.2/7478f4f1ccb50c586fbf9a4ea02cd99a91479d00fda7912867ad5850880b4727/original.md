```
generate_rand_design(d::Design, randomisations::Vector{Int}, shot_budget::Integer, experiment_shots::Integer; kwargs...)
generate_rand_design(d::Design, min_randomisations::Integer, target_shot_budget::Integer, experiment_shots::Integer; kwargs...)
```

Returns a [`RandDesign`](@ref) object describing a Pauli frame randomised experimental ensemble for the design `d`. Supply either the number of randomisations `randomisations` and shot budget `shot_budget` output by [`get_randomisations`](@ref), as well as the number of shots for each experiment `experiment_shots`, or the arguments of that function, namely the minimum number of randomisations `min_randomisations`, target shot budget `target_shot_budget`, and number of shots for each experiment `experiment_shots`.

# Arguments

  * `d::Design`: Experimental design.
  * `randomisations::Vector{Int}`: Number of randomisations for each tuple in the design.
  * `shot_budget::Integer`: Shot budget for the randomised experimental ensemble.
  * `min_randomisations::Integer`: Minimum number of randomisations for each tuple in the design.
  * `target_shot_budget::Integer`: Target shot budget for the randomised experimental ensemble.
  * `experiment_shots::Integer`: Number of shots for each experiment in the randomised experimental ensemble.

# Keyword arguments

  * `job_circuit_number::Integer = 200`: Number of circuits in each job.
  * `seed::Union{UInt64, Nothing} = nothing`: Random seed for the randomisation.
  * `diagnostics::Bool = false`: Whether to print diagnostics.
  * `save_data::Bool = false`: Whether to save the randomised design.
