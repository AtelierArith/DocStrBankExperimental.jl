```
get_hex_param(vertical_dist::Integer, horizontal_dist::Integer; kwargs...)
get_hex_param(dist::Integer; kwargs...)
```

Returns a [`HeavyHexParameters`](@ref) object that parameterises the syndrome extraction circuit of a heavy hex code.

Default gate layer times are estimated from IBM Torino in 2024.

# Arguments

  * `vertical_dist::Int`: Vertical distance of the code.
  * `horizontal_dist::Int`: Horizontal distance of the code.
  * `dist::Int`: Distance of the code; this is equivalent to setting `vertical_dist = dist` and `horizontal_dist = dist`.

# Keyword arguments

  * `flipped::Bool = false`: Whether to flip the ancilla qubit layout left to right.
  * `gate_type::Symbol = :cx`: Type of two-qubit gate used in the circuit.
  * `ancilla_measurement::Bool = true`: Whether to include mid-circuit reset.
  * `pad_identity::Bool = true`: Whether to pad layers with single-qubit identity gates.
  * `single_qubit_time::Real = 32`: Time taken to implement a single-qubit gate in nanoseconds.
  * `two_qubit_time::Real = 200`: Time taken to implement a two-qubit gate in nanoseconds.
  * `meas_reset_time::Real = 2500`: Time taken to perform measurement and reset at the end of the circuit in nanoseconds.
  * `meas_reset_time::Real = 2500`: Time taken to perform mid-circuit reset in nanoseconds.
