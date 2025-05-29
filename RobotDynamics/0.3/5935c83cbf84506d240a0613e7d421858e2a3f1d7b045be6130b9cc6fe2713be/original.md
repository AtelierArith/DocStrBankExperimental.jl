```
ẋ = dynamics(model, z::AbstractKnotPoint)
ẋ = dynamics(model, x, u, [t=0])
```

Compute the continuous dynamics of a forced dynamical given the states `x`, controls `u` and time `t` (optional).
