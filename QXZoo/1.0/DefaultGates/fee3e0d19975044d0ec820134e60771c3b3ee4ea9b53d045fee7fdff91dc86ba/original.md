```
c_r_z(q_target::Int, q_ctrl::Int, theta::Number)
```

Generate a controlled rotation about z (exp(iθz/2)) GateCall (GateCall2), controlled on the index `q_ctrl` applied to the target `q_target`

# Examples

```julia-repl
julia> QXZoo.DefaultGates.c_r_z( 0, 1, pi/4)
QXZoo.GateOps.GateCall2(QXZoo.GateOps.GateSymbolP(:c_r_z, 0, false, 0.7853981633974483), 0, 1, nothing)
```
