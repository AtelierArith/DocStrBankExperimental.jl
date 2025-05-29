```
get_control_qubits(gate::Gate{<:AbstractControlledGateSymbol})
```

Returns a list of the control qubits for a `gate`.

# Examples

```jldoctest
julia> get_control_qubits(toffoli(1, 4, 6))
2-element Vector{Int64}:
 1
 4

```
