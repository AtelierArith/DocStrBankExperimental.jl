```
c_r_y(q_target::Int, q_ctrl::Int, theta::Number)
```

Generate a controlled rotation about y (exp(iθy/2)) GateCall (GateCall2), controlled on the index `q_ctrl` applied to the target `q_target`.

# Examples

```julia-repl
julia> QXZoo.DefaultGates.c_r_y( 0, 1, pi/3)
QXZoo.GateOps.GateCall2(QXZoo.GateOps.GateSymbolP(:c_r_y, 0, false, 1.0471975511965976), 0, 1, nothing)
```
