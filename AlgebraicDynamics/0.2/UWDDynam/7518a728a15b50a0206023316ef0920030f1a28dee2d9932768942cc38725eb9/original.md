```
DelayResourceSharer{T}(nports, nstates, f, portmap)
```

An undirected open continuous system. The dynamics function `f` defines a DDE $\dot u(t) = f(u(t),h(t),p,t)$, where $h$ is a function giving the history of the system's state $u$ before the interval on which the solution will be computed begins (usually for $t < 0$). `f` should have signature $f(u,h,p,t)$, where $h$ is a function.
