```
reset(c::Circuit, target_qubits) -> Circuit
```

`c`に[`Reset`](@ref)オペレーターを追加し、ターゲットキュービットを`|0>`状態にアクティブリセットします。`Reset`操作は、[`Measure`](@ref)の後に適用してキュービットを再初期化し、中間回路測定後に再利用できるようにします。

# 例

```jldoctest
julia> circ = Circuit([(H, 0), (CNot, 0, 1)]);

julia> circ = reset(circ, 0);

julia> circ.instructions
3-element Vector{Braket.Instruction}:
 Braket.Instruction{H}(H(), QubitSet(0))
 Braket.Instruction{CNot}(CNot(), QubitSet(0, 1))
 Braket.Instruction{Reset}(Reset(), QubitSet(0))
```
