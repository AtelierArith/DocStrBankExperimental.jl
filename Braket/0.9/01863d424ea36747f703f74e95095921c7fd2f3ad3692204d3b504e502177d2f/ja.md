```
delay(c::Circuit, duration::Dates.Period, target_qubits) -> Circuit
```

`c`に[`Delay`](@ref)オペレーターを追加し、ターゲットとするすべての量子ビットが新しい操作が適用される前に`duration`だけ待機することを強制します。

# 例

```jldoctest
julia> circ = Circuit([(H, 0), (CNot, 0, 1)]);

julia> circ = delay(circ, Nanosecond(10), [0, 1]);

julia> circ.instructions
3-element Vector{Braket.Instruction}:
 Braket.Instruction{H}(H(), QubitSet(0))
 Braket.Instruction{CNot}(CNot(), QubitSet(0, 1))
 Braket.Instruction{Delay}(Delay(Nanosecond(10)), QubitSet(0, 1))
```
