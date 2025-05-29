```
c_z(q_target::Int, q_ctrl::Int)
```

Generate a controlled Pauli-x (two qubit) GateCall (GateCall2), controlled on the index `q_ctrl` applied to the target `q_target`.

# Examples

```julia-repl
julia> QXZoo.DefaultGates.c_z(0, 1)
QXZoo.GateOps.GateCall2(QXZoo.GateOps.GateSymbol(:c_z, 0, false), 0, 1, QXZoo.GateOps.GateSymbol(:z, 0, false))
```
