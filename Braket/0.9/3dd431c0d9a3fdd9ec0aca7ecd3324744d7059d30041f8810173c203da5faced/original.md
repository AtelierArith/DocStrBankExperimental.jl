```
measure(c::Circuit, target_qubits) -> Circuit
```

Add a [`Measure`](@ref) operator to `c`, ensuring only the targeted qubits are measured. A `Measure` operation can **only** be applied if the circuit does **not** contain any result types. If `c` has no qubits defined, or `target_qubits` are not within the qubit range of `c`, an `ArgumentError` is raised. If the circuit `c` contains any result types, or any of the  target qubits are already measured, an `ErrorException` is raised.

# Examples

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
