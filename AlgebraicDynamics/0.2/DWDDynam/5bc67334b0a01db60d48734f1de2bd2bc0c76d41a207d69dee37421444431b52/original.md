```
ContinuousMachine{T}(ninputs, nstates, noutputs, f, r)
```

A directed open continuous system. The dynamics function `f` defines an ODE $\dot u(t) = f(u(t),x(t),p,t)$, where $u$ is the state and $x$ captures the exogenous variables.

The readout function `r` may depend on the state, parameters and time, so it must be of the form $r(u,p,t)$. If it is left out, then $r=u$.
