```
Mie(; m, n, cutoff, use_neighbors, shortcut, σ_mixing, ϵ_mixing, weight_special)
```

The Mie generalized interaction between two atoms.

When `m` equals 6 and `n` equals 12 this is equivalent to the Lennard-Jones interaction. The potential energy is defined as

$$
V(r_{ij}) = C \varepsilon_{ij} \left[\left(\frac{\sigma_{ij}}{r_{ij}}\right)^n - \left(\frac{\sigma_{ij}}{r_{ij}}\right)^m\right]
$$

where

$$
C = \frac{n}{n - m} \left( \frac{n}{m} \right) ^\frac{m}{n - m}
$$
