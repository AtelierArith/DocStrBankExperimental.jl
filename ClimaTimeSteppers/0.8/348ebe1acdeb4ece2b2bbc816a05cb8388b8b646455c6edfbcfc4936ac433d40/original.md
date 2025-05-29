```
ForwardEulerODEFunction(f; jac_prototype, Wfact, tgrad)
```

An ODE function wrapper where `f(un, u, p, t, dt)` provides a forward Euler update

```
un .= u .+ dt * f(u, p, t)
```
