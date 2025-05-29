```
r_z(q_target::Int, theta::Number)
```

Generate a single qubit R_z(θ) GateCall (GateCall1) applied to the target qubit

# Examples

```julia-repl
julia> QXZoo.DefaultGates.r_z(3,pi/2)
QXZoo.GateOps.GateCall1(QXZoo.GateOps.GateSymbolP(:r_z, 0, false, 1.5707963267948966), 3)
```
