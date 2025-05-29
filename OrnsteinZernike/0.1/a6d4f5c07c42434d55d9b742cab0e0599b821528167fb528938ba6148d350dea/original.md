```
BomontBretonnet <: Closure
```

Implements the Bomont-Bretonnet closure $b(r) = \sqrt{1+2\gamma^*(r) + f \gamma^*(r)^2} - \gamma^*(r) - 1  $. Here  $\gamma^* = \gamma - u_{LR}$ , in which $ u_{LR}$ is the long range tail of the potential, and $f$ is a free parameter that can be determined with thermodynamic consistency.

Example:

```julia
closure = BomontBretonnet(0.5)
```

References:

Bomont, J. M., and J. L. Bretonnet. "A self-consistent integral equation: Bridge function and thermodynamic properties for the Lennard-Jones fluid." The Journal of chemical physics 119.4 (2003): 2188-2191.
