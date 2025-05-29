```
reset(c::Circuit, target_qubits) -> Circuit
```

Add a [`Reset`](@ref) operator to `c`, performing an active reset to the `|0>` state on the targeted qubits. A `Reset` operation can be applied after a [`Measure`](@ref) to re-initialize the qubit and allow it to be reused after mid-circuit measurement.

# Examples

```jldoctest
julia> circ = Circuit([(H, 0), (CNot, 0, 1)]);

julia> circ = reset(circ, 0);

julia> circ.instructions
3-element Vector{Braket.Instruction}:
 Braket.Instruction{H}(H(), QubitSet(0))
 Braket.Instruction{CNot}(CNot(), QubitSet(0, 1))
 Braket.Instruction{Reset}(Reset(), QubitSet(0))
```
