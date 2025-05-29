```
measure(c::Circuit, target_qubits) -> Circuit
```

`c`に[`Measure`](@ref)オペレーターを追加し、ターゲットキュービットのみが測定されるようにします。`Measure`操作は、回路に結果タイプが**含まれていない**場合に**のみ**適用できます。`c`に定義されたキュービットがない場合、または`target_qubits`が`c`のキュービット範囲内にない場合、`ArgumentError`が発生します。回路`c`に結果タイプが含まれている場合、またはターゲットキュービットのいずれかがすでに測定されている場合、`ErrorException`が発生します。

# 例

```jldoctest
julia> circ = Circuit([(H, 0), (CNot, 0, 1)]);

julia> circ = measure(circ, 0);

julia> circ.instructions
3-element Vector{Braket.Instruction}:
 Braket.Instruction{H}(H(), QubitSet(0))
 Braket.Instruction{CNot}(CNot(), QubitSet(0, 1))
 Braket.Instruction{Measure}(Measure(0), QubitSet(0))

julia> circ = Circuit([(H, 0), (CNot, 0, 1), (StateVector,)]);

julia> circ = measure(circ, 0);
ERROR: a circuit cannot contain both measure instructions and result types.
[...]

julia> circ = Circuit([(H, 0), (CNot, 0, 1)]);

julia> circ = measure(circ, [0, 1, 0]);
ERROR: cannot repeat qubit(s) in the same measurement.
[...]
```
