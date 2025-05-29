```
randompreparations(n::Int, npreps::Int;
                   local_input_state = "Pauli")
```

Generate `npreps` random input states to a quantum circuit. Each $n$-qubit input state is selected according to the following options:

  * `local_input_states = "Pauli"`: $D=6^n$ Pauli eigenstates
  * `local_input_states = "Tetra"`: $D=4^n$ 1-qubit SIC-POVM

The input states can also be set to a user-defined set, `local_input_states = ["A","B","C",...]`, assuming single-qubit states $|A\rangle$, $|B\rangle$ have been properly defined.
