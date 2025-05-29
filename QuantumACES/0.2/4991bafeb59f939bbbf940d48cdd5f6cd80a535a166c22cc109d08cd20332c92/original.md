```
CodeParameters
```

Code parameters for syndrome extraction circuits.

Note that these expect the qubits to be arranged such that the data qubits are first, followed by the ancilla qubits, and these parameters should be checked with [`check_code_parameters`](@ref).

# Fields

  * `qubits::Vector{Tuple{Int, Int}}`: Code qubit lattice locations.
  * `qubit_layout::Matrix{String}`: Diagram of the layout of the code qubits.
  * `inverse_indices::Dict{Tuple{Int, Int}, Int}`: Inverse mapping from the qubit lattice locations to their indices.
  * `data_indices::Vector{Int}`: Data qubit indices.
  * `ancilla_indices::Vector{Int}`: Ancilla qubit indices.
  * `ancilla_x_indices::Vector{Int}`: Ancilla X check qubit indices.
  * `ancilla_z_indices::Vector{Int}`: Ancilla Z check qubit indices.
  * `check_x_indices::Vector{Tuple{Vector{Int}, Vector{Int}}}`: Pairs of (ancilla, data) qubit indices for each of the X checks.
  * `check_z_indices::Vector{Tuple{Vector{Int}, Vector{Int}}}`: Pairs of (ancilla, data) qubit indices for each of the Z checks.
  * `init_x_indices::Vector{Int}`: Logical X initialisation qubit indices for which to initialise in the X basis.
  * `init_z_indices::Vector{Int}`: Logical Z initialisation qubit indices for which to initialise in the X basis.
  * `logical_x_indices::Vector{Int}`: Logical X operator qubit indices.
  * `logical_z_indices::Vector{Int}`: Logical Z operator qubit indices.
