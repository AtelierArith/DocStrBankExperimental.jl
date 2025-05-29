```
heisenbergtrottercircuit(nqubits::Integer, nlayers::Integer; topology=nothing)
```

Create a circuit that corresponds to a Trotterization of the Heisenberg Hamiltonian. A topology can be specified as a list of pairs of qubit indices. If no topology is specified, a bricklayer topology is used. Note that the gates are applied as layers of XX-YY-ZZ gates, not as layers of XX on all, then YY on all, then ZZ on all. On the bricklayer topology, these are equivalent.
