```
get_circuit(unrotated_param::UnrotatedPlanarParameters, noise_param::AbstractNoiseParameters; kwargs...)
```

Returns an unrotated planar code syndrome extraction circuit in the form of a [`Circuit`](@ref) object parameterised by the supplied circuit and noise parameters.

# Arguments

  * `unrotated_param::UnrotatedPlanarParameters`: Parameters for an unrotated planar code.
  * `noise_param::AbstractNoiseParameters`: Noise parameters for the circuit.

# Keyword arguments

  * `noisy_prep::Bool = false`: Whether to treat preparations as noisy and characterise the associated noise, defaulting to `false`; a full-rank design cannot be produced if both `noisy_prep` and `noisy_meas` are `true`.
  * `noisy_meas::Bool = true`: Whether to treat measurements as noisy and characterise the associated noise, defaulting to `true`; a full-rank design cannot be produced if both `noisy_prep` and `noisy_meas` are `true`.
  * `combined::Bool = haskey(noise_param.params, :combined) ? noise_param.params[:combined] : false,`: Whether to treat Pauli X, Y, and Z basis SPAM noise as the same.
  * `strict::Bool = false`: Whether to be strict about which gates count as estimable to relative precision.
