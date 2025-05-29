```
ExtendedRogersYoung <: Closure
```

Implements the extended Rogers-Young closure $b(r) = \ln(a\phi(r)^2 +  \phi(r) + 1) - γ(r) $.  Here, $\phi(r) = \frac{\exp(f(r)\gamma(r)) - 1}{f(r)}$, and $f(r)=1-\exp(-\alpha r)$, in which $\alpha$ is a free parameter,  that may be chosen such that thermodynamic consistency is achieved. Example:

```julia
closure = ExtendedRogersYoung(0.5, 0.5) # order is α, a
```

References: J. Chem. Phys. 128, 184507 (2008)
