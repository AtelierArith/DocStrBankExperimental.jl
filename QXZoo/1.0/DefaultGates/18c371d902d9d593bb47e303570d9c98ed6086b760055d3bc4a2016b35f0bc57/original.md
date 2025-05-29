```
r_phase(q_target::Int, theta::Number)
```

Generate a single qubit phase shift GateCall ( diag(1, exp(1im*theta)) , GateCall1) applied to the target qubit

# Examples

```julia-repl
julia> QXZoo.DefaultGates.r_phase(3,pi/2)
QXZoo.GateOps.GateCall1(QXZoo.GateOps.GateSymbolP(:r_phase, 0, false, 1.5707963267948966), 3)
```
