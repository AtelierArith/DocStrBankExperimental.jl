```
c_r_x(q_target::Int, q_ctrl::Int, theta::Number)
```

Generate a controlled rotation about x (exp(-iθx/2)) GateCall (GateCall2), controlled on the index `q_ctrl` applied to the target `q_target`.

# Examples

```julia-repl
julia> QXZoo.DefaultGates.c_r_x( 0, 1, pi/2)
QXZoo.GateOps.GateCall2(QXZoo.GateOps.GateSymbolP(:c_r_x, 0, false, 1.5707963267948966), 0, 1, nothing)
```
