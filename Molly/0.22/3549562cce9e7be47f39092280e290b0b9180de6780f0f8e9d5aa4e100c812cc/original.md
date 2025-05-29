```
Yukawa(; cutoff, use_neighbors, weight_special, coulomb_const, kappa)
```

The Yukawa electrostatic interaction between two atoms.

The potential energy is defined as

$$
V(r_{ij}) = \frac{q_i q_j}{4 \pi \varepsilon_0 r_{ij}} \exp(-\kappa r_{ij})
$$

and the force on each atom by 

$$
F(r_{ij}) = \frac{q_i q_j}{4 \pi \varepsilon_0 r_{ij}^2} \exp(-\kappa r_{ij})\left(\kappa r_{ij} + 1\right) \vec{r}_{ij}
$$
