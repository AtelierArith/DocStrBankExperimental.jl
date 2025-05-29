```
RotatedPlanarParameters
```

Parameters for the syndrome extraction circuit of a rotated planar code.

# Fields

  * `params::Dict{Symbol, Any}`: Dictionary of the circuit parameters described below.
  * `circuit_name::String`: Name of the circuit used for saving data.

# Parameters

  * `vertical_dist::Int`: Vertical (Z) distance of the code.
  * `horizontal_dist::Int`: Horizontal (X) distance of the code.
  * `check_type::Symbol`: Type of stabiliser used in the circuit, either `:xzzx` or `:standard`.
  * `gate_type::Symbol`: Type of two-qubit gate used in the circuit, either `:cx` or `:cz`.
  * `dynamically_decouple::Bool`: Whether to dynamically decouple the circuit; `true` is currently only supported for `:xzzx` and `:cz`.
  * `ancilla_measurement::Bool`: Whether to include mid-circuit ancilla measurements.
  * `pad_identity::Bool`: Whether to pad layers with single-qubit identity gates.
  * `layer_time_dict::Dict{Symbol, Float64}`: Dictionary of layer times.
