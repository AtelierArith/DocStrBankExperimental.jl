```
Circuit
```

Circuit information, including noise parameters.

# Fields

  * `circuit_param::AbstractCircuitParameters`: Circuit parameters.
  * `circuit::Vector{Layer}`: Circuit.
  * `circuit_tuple::Vector{Int}`: Tuple which arranges the order of the circuit layers; this is initialised as trivial.
  * `qubit_num::Int`: Number of qubits in the circuit.
  * `unique_layer_indices::Vector{Int}`: Unique non-measurement gate layer indices of the circuit.
  * `layer_types::Vector{Symbol}`: Types of the layers in the circuit, used for layer times and dynamical decoupling.
  * `layer_times::Vector{Float64}`: Times taken to implement each layer in the circuit, as well as measurement and reset.
  * `gates::Vector{Gate}`: Gates in the circuit arranged by the tuple.
  * `total_gates::Vector{Gate}`: Total gates in the circuit, including preparations if `noisy_prep` and measurements if `noisy_meas`.
  * `gate_data::GateData`: Gate data for the circuit.
  * `noise_param::AbstractNoiseParameters`: Noise parameters.
  * `gate_probabilities::Dict{Gate, Vector{Float64}}`: Pauli error probabilities for each gate, stored as a dictionary.
  * `gate_eigenvalues::Vector{Float64}`: Eigenvalues for each gate, stored as a vector whose order is determined by the gate order in `total_gates` and indexed by `gate_data`.
  * `noisy_prep::Bool`: Whether to treat preparations as noisy and characterise the associated noise, which should default to `false`; a full-rank design cannot be produced if both `noisy_prep` and `noisy_meas` are `true`.
  * `noisy_meas::Bool`: Whether to treat measurements as noisy and characterise the associated noise, which should default to `true`; a full-rank design cannot be produced if both `noisy_prep` and `noisy_meas` are `true`.
  * `extra_fields::Dict{Symbol, Any}`: Extra data for the circuit, including code parameters for syndrome extraction circuits stored as a `:code_param` field which is a [`CodeParameters`](@ref) object.
