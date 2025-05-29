```
generate_design(c::AbstractCircuit, tuple_set::Vector{Vector{Int}}; kwargs...)
generate_design(c::AbstractCircuit, tuple_set_data::TupleSetData; kwargs...)
generate_design(c::AbstractCircuit, d::Design; kwargs...)
generate_design(c::AbstractCircuit; kwargs...)
```

Returns a [`Design`](@ref) object containing all relevant information describing the experimental design, including the design matrix.

# Arguments

  * `c::AbstractCircuit`: Circuit for which the design matrix is to be generated.
  * `tuple_set::Vector{Vector{Int}}`: Tuple set arranging the circuit layers that is used to generate the experimental design.
  * `tuple_set_data::TupleSetData`: [`TupleSetData`](@ref) object that generates the tuple set.
  * `d::Design`: Old design object whose parameters are used to generate the design for the circuit `c`.

# Keyword arguments

  * `shot_weights::Union{Vector{Float64}, Nothing} = nothing`: Shot weights for each tuple in the set, which must add to 1. When `nothing`, automatically generates the default shot weights.
  * `N_warn::Integer = 10^5`: Number of circuit eigenvalues above which to warn the user about certain keyword argument choices.
  * `full_covariance::Bool = (c.gate_data.N < N_warn ? true : false)`: If `true`, generates parameters to construct the full covariance matrix, else if `false`, only generates parameters to construct the terms on the diagonal.
  * `add_circuit::Bool = false`: If tuple set data has not been supplied, the circuit itself is added to the repeat tuple set.
  * `repeat_points::Integer = 1`: If tuple set data has not been supplied, the each repeat number is augmented to have `repeat_points` repeat numbers.
  * `weight_experiments::Bool = true`: Whether to weight the shot weights for a tuple by the number of experiments for that tuple.
  * `diagnostics::Bool = false`: Whether to print diagnostic information.
  * `save_data::Bool = false`: Whether to save the design data.
