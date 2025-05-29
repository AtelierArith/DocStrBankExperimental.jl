```
HardSpheres
```

Implements the hard-sphere pair interaction for single component systems $ u(r) = \infty$ for $r < 1$ and $u(r) = 0$ for $r > 1$, or $u_{ij}(r) = \infty$ for $r < D_{ij}$ and $u_{ij}(r) = 0$ for $r > D_{ij}$ for mixtures.

For mixtures expects either a vector $D_i$ of diameters for each of the species in which case an additive mixing rule is used $\left(D_{ij} = (D_{i}+D_{j})/2\right)$  or a matrix $D_ij$ of pair diameters.

Example:

```example 1
potential = HardSpheres(1.0)
```

Example:

```example 2
potential = HardSpheres([0.8, 0.9, 1.0])
```

```example 3
Dij = rand(3,3)
potential = HardSpheres(Dij)
```
