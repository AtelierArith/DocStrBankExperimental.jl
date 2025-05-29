```
Circuit{N}(gates::Vector{<:CircuitGate}, mops::Union{Vector{<:MeasurementOperator},Nothing}=nothing)
```

Chain of quantum circuit gates in a circuit of `N` qubits. Constructed from vector of `CircuitGate` objects.
