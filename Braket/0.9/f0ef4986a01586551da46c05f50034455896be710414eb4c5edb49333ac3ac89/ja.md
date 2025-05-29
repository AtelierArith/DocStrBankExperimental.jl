```
barrier(c::Circuit, target_qubits) -> Circuit
```

`c`に[`Barrier`](@ref)演算子を追加し、すべてのターゲットキュービットが新しい操作が適用される前にバリアに到達することを強制します。

# 例

```jldoctest
julia> circ = Circuit([(H, 0), (CNot, 0, 1)]);

julia> circ = barrier(circ, [0, 1]);

julia> circ.instructions
3-element Vector{Braket.Instruction}:
 Braket.Instruction{H}(H(), QubitSet(0))
 Braket.Instruction{CNot}(CNot(), QubitSet(0, 1))
 Braket.Instruction{Barrier}(Barrier(), QubitSet(0, 1))
```
