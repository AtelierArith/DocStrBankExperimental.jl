```
appendSU4!(circuit, pair)
```

Append a layer of SU(4) gates to a circuit on a given pair of qubits. The SU(4) gate is decomposed via the KAK Decomposition into single-qubit Z-X-Z gates on each qubit, followed by XX-YY-ZZ gates and again single-qubit Z-X-Z gates, for a total of 15 Pauli gates.
