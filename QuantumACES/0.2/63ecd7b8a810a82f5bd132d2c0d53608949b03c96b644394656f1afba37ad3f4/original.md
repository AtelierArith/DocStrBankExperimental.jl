```
get_rotated_param(vertical_dist::Integer, horizontal_dist::Integer; kwargs...)
get_rotated_param(dist::Integer; kwargs...)
```

Returns a [`RotatedPlanarParameters`](@ref) object that parameterises the syndrome extraction circuit of a rotated planar code.

Default gate layer times are estimated from `Suppressing quantum errors by scaling a surface code logical qubit` by Google Quantum AI (2023).

# Arguments

  * `vertical_dist::Int`: Vertical (Z) distance of the code.
  * `horizontal_dist::Int`: Horizontal (X) distance of the code.
  * `dist::Int`: Distance of the code; this is equivalent to setting `vertical_dist = dist` and `horizontal_dist = dist`.

# Keyword arguments

  * `check_type::Symbol = :xzzx`: Type of stabiliser used in the circuit, either `:xzzx` or `:standard`.
  * `gate_type::Symbol = :cz`: Type of two-qubit gate used in the circuit, either `:cx` or `:cz`.
  * `dynamically_decouple::Bool = true`: Whether to dynamically decouple the circuit; `true` is currently only supported for `:xzzx` and `:cz`.
  * `ancilla_measurement::Bool = true`: Whether to include mid-circuit reset.
  * `pad_identity::Bool = true`: Whether to pad layers with single-qubit identity gates.
  * `single_qubit_time::Real = 29`: Time taken to implement a single-qubit gate in nanoseconds.
  * `two_qubit_time::Real = 29`: Time taken to implement a two-qubit gate in nanoseconds.
  * `meas_reset_time::Real = 660`: Time taken to perform measurement and reset at the end of the circuit in nanoseconds.
  * `dynamical_decoupling_time::Real = 29`: Time taken to implement a dynamical decoupling layer in nanoseconds.
  * `mid_reset_time::Real = 660`: Time taken to perform mid-circuit reset in nanoseconds.
