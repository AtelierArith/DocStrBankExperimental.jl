```
SoftCoreMeanSpherical <: Closure
```

Implements the soft core mean spherical closure $b(r) = \ln(\gamma^*(r) + 1) - \gamma^*(r)$. Here $\gamma^* = \gamma - u_{LR}$ , in which $u_{LR}$ is the long range tail of the potential.

Example:

```julia
closure = SoftCoreMeanSpherical()
```

References:
