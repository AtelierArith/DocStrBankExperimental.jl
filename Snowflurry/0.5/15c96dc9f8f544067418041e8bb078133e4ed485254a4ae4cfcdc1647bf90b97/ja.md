```
get_connected_qubits(instruction::AbstractInstruction)::AbstractVector{Int}
```

`instruction`が適用される量子ビットのインデックスを返します。

# 例

```jldoctest
julia> get_connected_qubits(control_z(1, 3))
2-element Vector{Int64}:
 1
 3

```
