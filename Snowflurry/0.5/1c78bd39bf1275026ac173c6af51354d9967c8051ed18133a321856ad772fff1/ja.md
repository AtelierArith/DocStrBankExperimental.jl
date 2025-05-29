```
get_target_qubits(gate::Gate{<:AbstractControlledGateSymbol})
```

`gate`のターゲットキュービットのリストを返します。

# 例

```jldoctest
julia> get_target_qubits(toffoli(1, 4, 6))
1-element Vector{Int64}:
 6

```
