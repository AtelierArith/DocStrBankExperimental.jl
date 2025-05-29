```
barrier(c::Circuit, target_qubits) -> Circuit
```

Add a [`Barrier`](@ref) operator to `c`, which forces all targeted qubits to reach the barrier before any new operations may be applied to any of them.

# Examples

```jldoctest
julia> circ = Circuit([(H, 0), (CNot, 0, 1)]);

julia> circ = barrier(circ, [0, 1]);

julia> circ.instructions
3-element Vector{Braket.Instruction}:
 Braket.Instruction{H}(H(), QubitSet(0))
 Braket.Instruction{CNot}(CNot(), QubitSet(0, 1))
 Braket.Instruction{Barrier}(Barrier(), QubitSet(0, 1))
```
