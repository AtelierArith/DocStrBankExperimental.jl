```
Buckingham(; cutoff, use_neighbors, shortcut, A_mixing, B_mixing,
           C_mixing, weight_special)
```

The Buckingham interaction between two atoms.

The potential energy is defined as

$$
V(r_{ij}) = A_{ij} \exp(-B_{ij} r_{ij}) - \frac{C_{ij}}{r_{ij}^6}
$$

and the force on each atom by

$$
\vec{F}_i = \left( A_{ij} B_{ij} \exp(-B_{ij} r_{ij}) - 6 \frac{C_{ij}}{r_{ij}^7} \right) \frac{\vec{r}_{ij}}{r_{ij}}
$$

The parameters are derived from the atom parameters according to

$$
\begin{aligned}
A_{ij} &= (A_{ii} A_{jj})^{1/2} \\
B_{ij} &= \frac{2}{\frac{1}{B_{ii}} + \frac{1}{B_{jj}}} \\
C_{ij} &= (C_{ii} C_{jj})^{1/2}
\end{aligned}
$$

so atoms that use this interaction should have fields `A`, `B` and `C` available.
