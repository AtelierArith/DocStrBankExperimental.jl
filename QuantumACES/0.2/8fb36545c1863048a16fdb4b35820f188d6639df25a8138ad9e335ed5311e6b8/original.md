```
get_stim_qiskit_ensemble(d_rand::RandDesign, qiskit_qubit_num::Integer, qiskit_qubit_map::Vector{Int})
```

Returns the Stim and Qiskit circuits for the randomised ensemble `d_rand`.

The Qiskit circuits act on `qiskit_qubit_num` qubits, which in general must be at least `maximum(qiskit_qubit_map) + 1`, and the mapping of the qubits upon which the circuits act to the qubits in the Qiskit circuits is controlled by `qiskit_qubit_map`, which is a vector whose length is the number of qubits upon which the circuits act.
