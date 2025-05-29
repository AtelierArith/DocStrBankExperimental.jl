```
CoulombSoftCore(; cutoff, α, λ, p, use_neighbors, σ_mixing, weight_special, coulomb_const)
```

The Coulomb electrostatic interaction between two atoms with a soft core.

The potential energy is defined as

$$
V(r_{ij}) = \frac{q_i q_j}{4 \pi \varepsilon_0 (r_{ij}^6 + \alpha  \sigma_{ij}^6  \lambda^p)^{\frac{1}{6}}}
$$

If $\alpha$ or $\lambda$ are zero this gives the standard [`Coulomb`](@ref) potential.
