```
kanemele(lat, t1, t2[; T, μ, field, statistics])
```

$\hat{H} = \sum_{i, j}^\text{adjacent} \left( t_1 c^\dagger_i c_j + h. c. \right) + \sum_{i, j}^\text{2-connected, counter-clockwise} \left( i \cdot t_2 c^\dagger_i σ_z c_j + h. c. \right)$

Generates a Kane-Mele hamiltonian operator on given lattice `lat`.

## Keyword arguments

  * `T`: The temperature of the system. Default is zero.
  * `μ`: The chemical potential. Use keyword `mu` as a synonym if Unicode input is not available.
  * `field`: The magnetic field. Default is `NoField()`.
  * `statistics` defines the particle statistics, either `FermiDirac` or `BoseEinstein`.
