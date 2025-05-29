```
ContinuousResourceSharer{T}(nports, nstates, f, portmap)
```

An undirected open continuous system. The dynamics function `f` defines an ODE $\dot u(t) = f(u(t),p,t)$,  where $u(t)$ has length `nstates`. `nports` is the number of exposed ports and `portmap` is a list of exposed states.  For example, if `portmap = [2,2,3]` then there are three ports which expose the state variables 2, 2, and 3 respectively.
