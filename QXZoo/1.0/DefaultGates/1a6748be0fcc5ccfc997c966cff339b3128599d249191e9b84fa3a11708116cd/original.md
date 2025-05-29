```
c_u(label::GateSymbol, q_target::Int, q_ctrl::Int)
```

Generate a controlled unitary (two qubit) GateCall (GateCall2), controlled on the index `q_ctrl` applied to the target `q_target`.

# Examples

```julia-repl
julia> QXZoo.DefaultGates.c_u(QXZoo.GateOps.GateSymbol(:myCU), 0, 1)
QXZoo.GateOps.GateCall2(QXZoo.GateOps.GateSymbol(:myCU, 0, false), 0, 1, nothing)
```
