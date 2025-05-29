```
c_r_phase(q_target::Int, q_ctrl::Int, theta::Real)
```

Generate a controlled phase rotation about (controlled [1 0; 0 exp(iθ)] GateCall (GateCall2), controlled on the index `q_ctrl` applied to the target `q_target`.

# Examples

```julia-repl
julia> QXZoo.DefaultGates.c_r_phase( 0, 1, pi/7 )
QXZoo.GateOps.GateCall2(QXZoo.GateOps.GateSymbolP(:c_r_phase, 0, false, 0.4487989505128276), 0, 1, nothing)
```
