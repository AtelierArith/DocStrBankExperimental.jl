```
getparameterindices(circuit, ::PauliRotation, gate_symbols::Vector{Symbol}))
```

Utility function to get the parameter indices of `PauliRotation` gates with symbol `gate_symbols`. For example, `getparameterindices(circuit, PauliRotation, [:X])`.
