```
manifold_dimension(::Tucker)
```

The dimension of the manifold of $N_1×\dots×N_D$ tensors of multilinear rank $(R_1, \dots, R_D)$, i.e.

$$
\mathrm{dim}(\mathcal{M}) = \prod_{d=1}^D R_d + \sum_{d=1}^D R_d (N_d - R_d).
$$
