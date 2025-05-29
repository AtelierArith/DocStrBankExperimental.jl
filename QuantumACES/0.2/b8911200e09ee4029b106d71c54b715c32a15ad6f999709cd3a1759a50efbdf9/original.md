```
Layer
```

A layer of gates in a stabiliser circuit. Gates in a layer are simultaneously implemented by the device, and act on disjoint sets of qubits such that they trivially commute with each other.

# Fields

  * `layer::Vector{Gate}`: The gates in the layer.
  * `qubit_num::Int16`: The number of qubits in the circuit.
