```
VompeMartynov <: Closure
```

Implements the Vompe-Martynov closure $b(r) = \sqrt{1+2\gamma^*(r) } - \gamma^*(r) - 1 $. Here  $\gamma^* = \gamma - u_{LR}$ , in which $ u_{LR}$ is the long range tail of the potential, and $\alpha$ is a free parameter that can be determined with thermodynamic consistency.

Example:

```julia
closure = VompeMartynov()
```

References:

Vompe, A. G., and G. A. Martynov. "The bridge function expansion and the self‐consistency problem of the Ornstein–Zernike equation solution." The Journal of chemical physics 100.7 (1994): 5249-5258.
