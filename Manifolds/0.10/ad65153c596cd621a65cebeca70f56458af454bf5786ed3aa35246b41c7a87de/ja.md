```
manifold_dimension(::Tucker)
```

多線形ランク $(R_1, \dots, R_D)$ の $N_1×\dots×N_D$ テンソルの多様体の次元、すなわち

$$
\mathrm{dim}(\mathcal{M}) = \prod_{d=1}^D R_d + \sum_{d=1}^D R_d (N_d - R_d).
$$
