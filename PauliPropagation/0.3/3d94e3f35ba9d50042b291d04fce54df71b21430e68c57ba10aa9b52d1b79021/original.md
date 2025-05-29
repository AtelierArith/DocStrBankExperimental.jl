```
tfitrottercircuit(nqubits::Integer, nlayers::Integer; topology=nothing, start_with_ZZ=true)
```

Create a circuit that corresponds to a Trotterization of the transverse-field Ising Hamiltonian.  A topology can be specified as a list of pairs of qubit indices. If no topology is specified, a bricklayer topology is used. If `start_with_ZZ` is set to `true`, the circuit starts with a layer of ZZ gates, else with a layer of X gates. This is relevant depending on the initial state.
