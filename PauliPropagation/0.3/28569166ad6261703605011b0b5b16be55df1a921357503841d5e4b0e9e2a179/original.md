```
hardwareefficientcircuit(nqubits::Integer, nlayers::Integer; topology=nothing)
```

Create a hardware-efficient circuit consisting of layers of single-qubit X-Z-X Pauli gates and YY entangling gates. A topology can be specified as a list of pairs of qubit indices.  If no topology is specified, a bricklayer topology is used.
