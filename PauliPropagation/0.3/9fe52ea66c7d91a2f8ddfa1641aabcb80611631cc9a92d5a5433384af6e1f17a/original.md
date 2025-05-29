```
bricklayertopology(nqubits::Integer; periodic=false)
```

Create the topology of a so-called 1D bricklayer circuit on `nqubits` qubits. It consists of two sublayers connecting odd-even and eve-odd qubit indices, respectively. If `periodic` is set to `true`, the last qubit is connected to the first qubit.
