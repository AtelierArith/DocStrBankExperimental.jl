```
su4circuit(nqubits::Integer, nlayers::Integer; topology=nothing)
```

Create a circuit that consists of layers of SU(4) gates on a given topology.  SU(4) gates are decomposed via the KAK Decomposition into single-qubit Z-X-Z gates on each qubit, followed by XX-YY-ZZ gates and again single-qubit Z-X-Z gates, for a total of 15 Pauli gates. A topology can be specified as a list of pairs of qubit indices. If no topology is specified, a bricklayer topology is used.
