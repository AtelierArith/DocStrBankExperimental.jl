A constant dictionary `GATES` containing common quantum gate matrices as complex-valued matrices. Each gate is represented by its unitary matrix.

  * `GATES[:I]` - Identity: Leaves the state unchanged.
  * `GATES[:X]` - Pauli-X (NOT): Flips the qubit state.
  * `GATES[:Y]` - Pauli-Y: Rotates the qubit state around the Y-axis of the Bloch sphere.
  * `GATES[:Z]` - Pauli-Z: Flips the phase of the qubit state.
  * `GATES[:H]` - Hadamard: Creates superposition by transforming basis states.
  * `GATES[:CX]` - Controlled-X (CNOT): Flips the 2nd qubit (target) if the first qubit (control) is |1⟩.
  * `GATES[:CZ]` - Controlled-Z (CZ): Flips the phase of the 2nd qubit (target) if the 1st qubit (control) is |1⟩.
  * `GATES[:XI]` - Complex: A gate for complex operations.
  * `GATES[:sqrtiSWAP]` - Square root of iSWAP: Partially swaps two qubits with a phase.
