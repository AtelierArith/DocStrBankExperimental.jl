```
get_connected_qubits(instruction::AbstractInstruction)::AbstractVector{Int}
```

Returns the indices of the qubits on which the `instruction` is applied.

# Examples

```jldoctest
julia> get_connected_qubits(control_z(1, 3))
2-element Vector{Int64}:
 1
 3

```
