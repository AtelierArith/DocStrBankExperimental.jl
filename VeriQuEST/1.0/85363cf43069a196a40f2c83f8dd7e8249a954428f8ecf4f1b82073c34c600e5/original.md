```
init_qubit(::TrapQubit)::Float64
```

This function is used to initialize the qubit in the meta graph.  The state is not given, but the angle for the plus phase state for a trap qubit is returned.

# Arguments

  * `trap::TrapQubit`: The TrapQubit object.

# Returns

  * A Float64 representing the angle for the plus phase state for a trap qubit.

# Examples

```julia
trap = TrapQubit()
angle = init_qubit(trap)
```
