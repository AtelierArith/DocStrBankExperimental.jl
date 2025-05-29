```
display_circuit(stim_circuit_string::String; without_noise::Bool = true)
display_circuit(qiskit_circuit::Py)
```

Displays the supplied Stim or Qiskit circuit `stim_circuit_string` or `qiskit_circuit`, and if `without_noise` is `true`, displays the Stim circuit without Pauli noise channels. Be careful: Python arrays stored in PythonCall index from 0, so it is easy to index into the wrong Qiskit circuit.
