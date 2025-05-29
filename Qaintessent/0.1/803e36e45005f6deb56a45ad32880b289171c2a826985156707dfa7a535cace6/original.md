```
sparse_matrix(m::MeasurementOperator{M,G}, N::Integer=0) where {M,G}
```

returns matrix representation of a `MeasurementOperator{M,G}` object that can applied to a state vector of `N` qubits.
