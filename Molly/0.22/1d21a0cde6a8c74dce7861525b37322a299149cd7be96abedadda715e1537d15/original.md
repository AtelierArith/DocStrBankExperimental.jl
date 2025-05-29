```
LennardJonesSoftCore(; cutoff, α, λ, p, use_neighbors, shortcut, σ_mixing, ϵ_mixing,
                     weight_special)
```

The Lennard-Jones 6-12 interaction between two atoms with a soft core.

The potential energy is defined as

$$
V(r_{ij}) = 4\varepsilon_{ij} \left[\left(\frac{\sigma_{ij}}{r_{ij}^{\text{sc}}}\right)^{12} - \left(\frac{\sigma_{ij}}{r_{ij}^{\text{sc}}}\right)^{6}\right]
$$

and the force on each atom by

$$
\vec{F}_i = 24\varepsilon_{ij} \left(2\frac{\sigma_{ij}^{12}}{(r_{ij}^{\text{sc}})^{13}} - \frac{\sigma_{ij}^6}{(r_{ij}^{\text{sc}})^{7}}\right) \left(\frac{r_{ij}}{r_{ij}^{\text{sc}}}\right)^5 \frac{\vec{r}_{ij}}{r_{ij}}
$$

where

$$
r_{ij}^{\text{sc}} = \left(r_{ij}^6 + \alpha \sigma_{ij}^6 \lambda^p \right)^{1/6}
$$

If $\alpha$ or $\lambda$ are zero this gives the standard [`LennardJones`](@ref) potential.
