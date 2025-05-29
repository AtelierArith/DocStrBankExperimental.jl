```
get_num_connected_qubits(gate::AbstractGateSymbol)::Int
```

Returns the number of qubits to which the `gate` is applied.

# Examples

```jldoctest
julia> get_num_connected_qubits(get_gate_symbol(control_z(1, 3)))
2

```
