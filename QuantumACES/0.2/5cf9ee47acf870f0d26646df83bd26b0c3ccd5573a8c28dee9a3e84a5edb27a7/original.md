```
get_circuit(circuit::Vector{Layer}, layer_types::Vector{Symbol}, layer_times::Vector{Float64}, noise_param::AbstractNoiseParameters; kwargs...)
```

Returns a [`Circuit`](@ref) object given the supplied circuit and noise parameters.

# Arguments

  * `circuit::Vector{Layer}`: Circuit.
  * `layer_types::Vector{Symbol}`: Types of the layers in the circuit.
  * `layer_times::Vector{Float64}`: Times taken to implement each layer in the circuit, as well as measurement and reset.
  * `noise_param::AbstractNoiseParameters`: Noise parameters for the circuit.

# Keyword arguments

  * `circuit_param::AbstractCircuitParameters = EmptyCircuitParameters()`: Circuit parameters.
  * `extra_fields::Dict{Symbol, Any} = Dict{Symbol, Any}()`: Extra fields, including for [`CodeParameters`](@ref).
  * `noisy_prep::Bool = false`: Whether to treat preparations as noisy and characterise the associated noise; a full-rank design cannot be produced if both `noisy_prep` and `noisy_meas` are `true`.
  * `noisy_meas::Bool = true`: Whether to treat measurements as noisy and characterise the associated noise; a full-rank design cannot be produced if both `noisy_prep` and `noisy_meas` are `true`.
  * `combined::Bool = haskey(noise_param.params, :combined) ? noise_param.params[:combined] : false,`: Whether to treat Pauli X, Y, and Z basis SPAM noise as the same.
  * `strict::Bool = false`: Whether to be strict about which gates count as estimable to relative precision.
