```
Mapping
```

Mapping of a Pauli operator by some circuit.

# Fields

  * `initial::Pauli`: Initial Pauli operator before the action of the circuit.
  * `final::Pauli`: Final Pauli operator after the action of the circuit.
  * `design_row::SparseVector{Int32, Int32}`: Design matrix row for the circuit eigenvalue corresponding to the initial Pauli and the circuit used for the mapping.
  * `spread_track::Vector{Vector{Int16}}`: Track of the support of the Pauli as it is acted upon by the layers of the circuit.
