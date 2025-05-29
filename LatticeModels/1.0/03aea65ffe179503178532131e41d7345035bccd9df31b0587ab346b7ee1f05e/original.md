```
qwz(m[; T, μ, field, statistics])
qwz(lat[, m; T, μ, field, statistics])
```

$\hat{H} = \sum_i^\text{sites} m_i c^\dagger_i \sigma_z c_i + \sum_i^\text{sites} \left( c^\dagger_{i + \hat{x}} \frac{\sigma_z - i \sigma_x}{2} c_i + c^\dagger_{i + \hat{y}} \frac{\sigma_z - i \sigma_y}{2} c_i + h. c. \right)$

Generates a QWZ model hamiltonian operator on given square lattice `lat`.

## Arguments

  * `m` (either a `LatticeValue` or a number) defines the $m_i$ factors

## Keyword arguments

  * `T`: The temperature of the system. Default is zero.
  * `μ`: The chemical potential. Use `mu` as a synonym if Unicode input is not available.
  * `field`: The magnetic field. Default is `NoField()`.
  * `statistics` defines the particle statistics, either `FermiDirac` or `BoseEinstein`.
