```
get_num_connected_qubits(gate::AbstractGateSymbol)::Int
```

`gate`が適用される量子ビットの数を返します。

# 例

```jldoctest
julia> get_num_connected_qubits(get_gate_symbol(control_z(1, 3)))
2

```
