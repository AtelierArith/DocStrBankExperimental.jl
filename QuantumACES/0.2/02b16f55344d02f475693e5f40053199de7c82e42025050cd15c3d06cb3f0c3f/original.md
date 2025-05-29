```
HeavyHexParameters
```

Parameters for the syndrome extraction circuit of a heavy hex code.

# Fields

  * `params::Dict{Symbol, Any}`: Dictionary of the circuit parameters described below.
  * `circuit_name::String`: Name of the circuit used for saving data.

# Parameters

  * `vertical_dist::Int`: Vertical (Z) distance of the code.
  * `horizontal_dist::Int`: Horizontal (X) distance of the code.
  * `flipped::Bool`: Whether ancilla qubit layout is flipped left to right.
  * `gate_type::Symbol`: Type of two-qubit gate used in the circuit, which must be `:cx`.
  * `ancilla_measurement::Bool`: Whether to include mid-circuit ancilla measurements.
  * `pad_identity::Bool`: Whether to pad layers with single-qubit identity gates.
  * `layer_time_dict::Dict{Symbol, Float64}`: Dictionary of layer times.
