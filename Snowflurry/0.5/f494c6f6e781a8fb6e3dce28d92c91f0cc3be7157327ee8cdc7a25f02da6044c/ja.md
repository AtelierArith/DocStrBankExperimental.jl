```
get_control_qubits(gate::Gate{<:AbstractControlledGateSymbol})
```

`gate`の制御キュービットのリストを返します。

# 例

```jldoctest
julia> get_control_qubits(toffoli(1, 4, 6))
2-element Vector{Int64}:
 1
 4

```
