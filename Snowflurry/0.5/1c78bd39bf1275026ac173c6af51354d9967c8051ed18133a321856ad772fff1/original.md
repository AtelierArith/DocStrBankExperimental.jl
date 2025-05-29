```
get_target_qubits(gate::Gate{<:AbstractControlledGateSymbol})
```

Returns a list of the target qubits for a `gate`.

# Examples

```jldoctest
julia> get_target_qubits(toffoli(1, 4, 6))
1-element Vector{Int64}:
 6

```
