```
PassiveTracerEquations(flow_equations; n_tracers)
```

Adds passive tracers to the `flow_equations`. The tracers are advected by the flow velocity. These work for arbitrary dimensions with arbitrary numbers of tracers `n_tracers`, for conservative and non-conservative equations. For one dimension, with  one tracer $\chi$ and flow with density and velocity $\rho, v$ respectively, the equation of the passive tracer is

$$
\frac{\partial \rho \chi}{\partial t} + \frac{\partial}{\partial x} \left( \rho v \chi \right) = 0
$$
