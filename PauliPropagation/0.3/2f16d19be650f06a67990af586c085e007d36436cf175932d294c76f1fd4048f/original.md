```
getparameterindices(circuit, GateType<:ParametrizedGate)
```

Utility function to get the parameter indices of gates of type `GateType` in a circuit. This naturally only works for gates that subtype `ParametrizedGate`.
