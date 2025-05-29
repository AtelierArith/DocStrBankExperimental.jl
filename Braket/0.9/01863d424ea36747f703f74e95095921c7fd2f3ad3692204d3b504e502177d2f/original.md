```
delay(c::Circuit, duration::Dates.Period, target_qubits) -> Circuit
```

Add a [`Delay`](@ref) operator to `c`, which forces all targeted qubits to wait for `duration` before any new operations may be applied to any of them.

# Examples

```jldoctest
julia> circ = Circuit([(H, 0), (CNot, 0, 1)]);

julia> circ = delay(circ, Nanosecond(10), [0, 1]);

julia> circ.instructions
3-element Vector{Braket.Instruction}:
 Braket.Instruction{H}(H(), QubitSet(0))
 Braket.Instruction{CNot}(CNot(), QubitSet(0, 1))
 Braket.Instruction{Delay}(Delay(Nanosecond(10)), QubitSet(0, 1))
```
