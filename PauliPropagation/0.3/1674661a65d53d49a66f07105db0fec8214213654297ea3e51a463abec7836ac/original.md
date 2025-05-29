```
FrozenGate(gate::ParametrizedGate, parameter::Number)
```

A `StaticGate` that wraps a `ParametrizedGate` with a fixed parameter. These are used to fix the parameter of `ParametrizedGate` at the time of circuit construction. This can be convenient but might exclude this parameter from being, e.g., differentiated by external libraries.
