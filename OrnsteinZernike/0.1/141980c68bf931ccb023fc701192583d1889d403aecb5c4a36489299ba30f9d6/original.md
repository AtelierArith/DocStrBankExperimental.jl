```
ChoudhuryGhosh <: Closure
```

Implements the Choudhury-Ghosh closure $b(r) = -\frac{-\gamma^*(r)^2}{2(1+\alpha \gamma^*(r))} $ for $\gamma^*(r) >0$, and $b(r)=-\gamma^*(r)^2/2$ otherwise. Here  $\gamma^* = \gamma - u_{LR}$ , in which $ u_{LR}$ is the long range tail of the potential, and $\alpha$ is a free parameter that  is determined by an empirical relation.

Example:

```julia
α(ρ) = 1.01752 - 0.275ρ # see the reference for this empirical relation
closure = ChoudhuryGhosh(α(0.4))
```

References:

Choudhury, Niharendu, and Swapan K. Ghosh. "Integral equation theory of Lennard-Jones fluids: A modified Verlet bridge function approach." The Journal of chemical physics 116.19 (2002): 8517-8522.
