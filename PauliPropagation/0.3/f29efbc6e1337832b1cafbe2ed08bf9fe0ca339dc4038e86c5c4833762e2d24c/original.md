```
efficientsu2circuit(nqubits::Integer, nlayers::Integer; topology=nothing)
```

Create a hardware-efficient circuit consisting of layers of single-qubit Y-Z Pauli gates and CNOT entangling gates. A topology can be specified as a list of pairs of qubit indices. If no topology is specified, a bricklayer topology is used.
