```
DiscreteMachine{T}(ninputs, nstates, noutputs, f, r)
```

A directed open discrete dynamical system. The dynamics function `f` defines a discrete update rule $u_{n+1} = f(u_n, x_n, p, t)$, where $u_n$ is the state and $x_n$ is the value of the exogenous variables at the $n$th time step.

The readout function `r` may depend on the state, parameters and time step, so it must be of the form $r(u_n,p,n)$. If it is left out, then $r_n=u_n$.
