```
RogersYoung <: Closure
```

Implements the Rogers-Young closure $b(r) = \ln(\frac{\exp(f(r)\gamma(r)) - 1}{f(r)} + 1) - γ(r) $.  Here $f(r)=1-\exp(-\alpha r)$, in which $\alpha$ is a free parameter,  that may be chosen such that thermodynamic consistency is achieved. Example:

```julia
closure = RogersYoung(0.5)
```

References:
