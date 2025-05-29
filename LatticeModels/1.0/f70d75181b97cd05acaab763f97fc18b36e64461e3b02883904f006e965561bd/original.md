```
haldane(lat, t1, t2[, m=0; T, μ, field, statistics])
```

$\hat{H} = \sum_i^\text{sublattice A} m c^\dagger_i c_i + \sum_j^\text{sublattice B} m c^\dagger_j c_j + \sum_{i, j}^\text{adjacent} \left( t_1 c^\dagger_i c_j + h. c. \right) + \sum_{i, j}^\text{2-connected, counter-clockwise} \left( i \cdot t_2 c^\dagger_i c_j + h. c. \right)$

Generates a Haldane topological insulator hamiltonian operator on given lattice `lat`.

## Keyword arguments

  * `T`: The temperature of the system. Default is zero.
  * `μ`: The chemical potential. Use `mu` as a synonym if Unicode input is not available.
  * `field`: The magnetic field. Default is `NoField()`.
  * `statistics` defines the particle statistics, either `FermiDirac` or `BoseEinstein`.
