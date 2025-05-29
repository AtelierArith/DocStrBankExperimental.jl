```
Gate
```

A gate in a stabiliser circuit.

# Fields

  * `type::String`: String describing the gate type.
  * `index::Int32`: The index labelling the unique layer occurrences of the gate in a circuit.
  * `targets::Vector{Int16}`: The qubit target or targets of the gate.

# Supported gates

  * `H`: Hadamard gate.
  * `S`: Phase gate.
  * `S_DAG`: Conjugate phase gate.
  * `CX` or `CNOT`: Controlled-X gate; the first qubit is the control and the second qubit is the target.
  * `CZ`: Controlled-Z gate.
  * `I`: Identity gate.
  * `Z`: Pauli Z gate.
  * `X`: Pauli X gate.
  * `Y`: Pauli Y gate.
  * `II`: Two-qubit identity gate.
  * `AB`: Two-qubit Pauli gate, where `A` and `B` are Paulis `Z`, `X`, or `Y`.
  * `SQRT_AB`: Two-qubit Pauli rotation, where `A` and `B` are Paulis `Z`, `X`, or `Y`.
  * `SQRT_AB_DAG` : Two-qubit Pauli rotation, where `A` and `B` are Paulis `Z`, `X`, or `Y`.
  * `PZ`: Prepare the Pauli Z eigenstate.
  * `PX`: Prepare the Pauli X eigenstate.
  * `PY`: Prepare the Pauli Y eigenstate.
  * `M` or `MZ`: Measure in the computational Pauli Z basis.
  * `MX`: Measure in the Pauli X basis.
  * `MY`: Measure in the Pauli Y basis.
  * `R`: Reset in the computational Z basis.
