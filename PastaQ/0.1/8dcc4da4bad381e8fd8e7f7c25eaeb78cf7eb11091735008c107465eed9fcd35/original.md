```
fullpreparations(n::Int; local_input_states = "Pauli")
```

Generate the full set of $n$-qubit input states built out of a collection of $D=M^n$ states out of $M$ single-qubit states. Predefined options:

  * `local_input_states = "Pauli"`: $D=6^n$ Pauli eigenstates
  * `local_input_states = "Tetra"`: $D=4^n$ 1-qubit SIC-POVM
