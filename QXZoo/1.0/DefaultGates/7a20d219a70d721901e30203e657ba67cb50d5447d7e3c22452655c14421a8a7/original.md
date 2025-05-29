```
u(label::String, q_target::Int)
```

Generate a single qubit arbitrary unitary GateCall (GateCall1) applied to the  target qubit

# Examples

```julia-repl
julia> QXZoo.DefaultGates.u("mygate", 1)
QXZoo.GateOps.GateCall1(QXZoo.GateOps.GateSymbol(:mygate, 0, false), 0)
```
