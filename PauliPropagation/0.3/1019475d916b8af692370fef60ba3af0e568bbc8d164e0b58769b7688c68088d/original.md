```
getparameterindices(circuit, ::PauliRotation, gate_symbols::Vector{Symbol}), qinds::Vector{Int})
```

Utility function to get the parameter indices of `PauliRotation` gates with symbol `gate_symbols` acting on the qubits `qinds`. For example, `getparameterindices(circuit, PauliRotation, [:X], [1])`.
