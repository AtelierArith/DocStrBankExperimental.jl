```
StepsizeCallback(; cfl=1.0, interval = 1)
```

Set the time step size according to a CFL condition with CFL number `cfl` if the time integration method isn't adaptive itself.

The supplied keyword argument `cfl` must be either a `Real` number or a function of time `t` returning a `Real` number. By default, the timestep will be adjusted at every step. For different values of `interval`, the timestep will be adjusted every `interval` steps.
