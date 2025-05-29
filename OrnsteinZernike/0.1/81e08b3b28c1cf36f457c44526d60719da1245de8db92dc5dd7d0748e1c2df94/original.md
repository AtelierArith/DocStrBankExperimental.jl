ZerahHansen <: Closure

Implements the Zerah-Hansen (HMSA) (HNC-SMSA) closure $b(r) = \ln(\frac{\exp(f(r)\gamma^*(r)) - 1}{f(r)} + 1) - γ^*(r) $. Here  $\gamma^* = \gamma - u_{LR}$ , in which $ u_{LR}$ is the long range tail of the potential,  and $f(r)=1-\exp(-\alpha r)$, in which $\alpha$ is a free parameter,  that may be chosen such that thermodynamic consistency is achieved.

Example:

```julia
closure = ZerahHansen(0.5)
```

References:

Zerah, Gilles, and Jean‐Pierre Hansen. "Self‐consistent integral equations for fluid pair distribution functions: Another attempt." The Journal of chemical physics 84.4 (1986): 2336-2343.
