```
u_modified!(i::DEIntegrator,bool)
```

Sets `bool` which states whether a change to `u` occurred, allowing the solver to handle the discontinuity. By default, this is assumed to be true if a callback is used. This will result in the re-calculation of the derivative at `t+dt`, which is not necessary if the algorithm is FSAL and `u` does not experience a discontinuous change at the end of the interval. Thus if `u` is unmodified in a callback, a single call to the derivative calculation can be eliminated by `u_modified!(integrator,false)`.
