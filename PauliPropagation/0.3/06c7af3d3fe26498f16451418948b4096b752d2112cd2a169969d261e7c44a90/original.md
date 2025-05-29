```
PauliSum(nqubits::Int, terms::Dict)
```

`PauliSum` is a `struct` that represents a sum of Pauli strings acting on `nqubits` qubits. It is a wrapper around a dictionary Dict(Pauli string => coefficient}, where the Pauli strings are typically unsigned Integers for efficiency reasons.
