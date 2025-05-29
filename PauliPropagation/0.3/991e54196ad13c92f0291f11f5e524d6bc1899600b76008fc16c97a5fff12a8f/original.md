```
composecliffordmaps(circuit::Vector{CliffordGate})
```

Compose a circuit of Clifford gates into a single Clifford map. The length of the map is `4^nq``where`nq`is the maximum qubit index in the circuit. The resulting clifford map can be added to the global`clifford_map`with a custom Clifford gate name. The maximum number of qubits is 4 due to current restrictions of`UInt8`. Even if all gates only act on one qubit, that qubit index will determine the dimensionality of the map.
