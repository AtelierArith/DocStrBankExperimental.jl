```
bosehubbard([type, ]lat, N[; U, T, t1, t2, t3, field])
```

$\hat{H} = \sum_{i,j}^\text{sites} t_{ij} c^\dagger_i c_j + \sum_i^\text{sites} \frac{U}{2} \hat{n}_i (\hat{n}_i - 1)$

Generates a Bose-Hubbard model hamiltonian on given lattice `lat`.

## Arguments

  * `type`: The element type of the resulting operator. Default is `ComplexF64`.
  * `N`: The number of particles.

## Keyword arguments

  * `t1`, `t2`, `t3` denote the coefficient on first, second and third hoppings respectively.   By default `t1` is equal to one, the rest are zero.
  * `U`: The interaction strength. Default is zero.
  * `T`: The temperature of the system. Default is zero.
  * `field`: The magnetic field. Default is `NoField()`.
