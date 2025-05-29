```
ff_controller(l::LQGProblem, L = lqr(l), K = kalman(l))
```

Return the feedforward controller $C_{ff}$ that maps references to plant inputs: $u = C_{fb}y + C_{ff}r$

The following should hold

```
Cff = RobustAndOptimalControl.ff_controller(l)
Cfb = observer_controller(l)
Gcl = feedback(system_mapping(l), Cfb) * Cff # Note the comma in feedback, P/(I + PC) * Cff
dcgain(Gcl) ≈ I # Or some I-like non-square matrix 
```

Note, if [`extended_controller`](@ref) is used, the DC-gain compensation above cannot be used. The [`extended_controller`](@ref) assumes that the references enter like `u = L(xᵣ - x̂)`. 

See also [`observer_controller`](@ref).
