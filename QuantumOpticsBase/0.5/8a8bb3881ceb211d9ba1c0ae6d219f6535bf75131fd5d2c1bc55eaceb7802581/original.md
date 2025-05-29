```
LazyKet(b, kets)
```

Lazy implementation of a tensor product of kets.

The subkets are stored in the `kets` field. The main purpose of such a ket are simple computations for large product states, such as expectation values. It's used to compute numeric initial states in QuantumCumulants.jl (see QuantumCumulants.initial_values).
