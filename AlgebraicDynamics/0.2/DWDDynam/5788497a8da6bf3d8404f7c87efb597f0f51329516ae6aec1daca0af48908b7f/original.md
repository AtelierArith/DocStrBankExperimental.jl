```
DelayMachine{T}(ninputs, nstates, noutputs, f, r)
```

A delay open continuous system. The dynamics function `f` defines an ODE $\dot u(t) = f(u(t), x(t), h(p,t), p, t)$, where $u$ is the state, $x$ captures the exogenous variables, and $h$ is a history function.

The readout function `r` may depend on the state, history, parameters and time, so it has the signature $r(u,h,p,t)$. If it is left out, then $r=u$.
