```
r_y(q_target::Int, theta::Number)
```

Generate a single qubit R_y(θ) GateCall (GateCall1) applied to the target qubit.

# Examples

```julia-repl
julia> QXZoo.DefaultGates.r_y(3,pi/2)
QXZoo.GateOps.GateCall1(QXZoo.GateOps.GateSymbolP(:r_y, 0, false, 1.5707963267948966), 3)
```
