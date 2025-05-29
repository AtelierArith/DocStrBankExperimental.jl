```
densitymatrix(eig::Eigensystem[; T=0, μ, N, statistics, info=true])
```

Creates an `Operator` representing a equilibrium density matrix, given the eigensystem `eig` of the Hamiltonian.

The resulting distribution will be Fermi-Dirac or Bose-Einstein if the `statistics` is specified, otherwise the Gibbs distribution will be used.

## Keyword arguments

  * `T` is the temperature of the system. Default is zero.
  * `μ` is the chemical potential. Use `mu` as a synonym if Unicode input is not available.
  * `N` is the number of particles. If specified, the chemical potential is found automatically.
  * `statistics` defines the particle statistics, either `FermiDirac` or `BoseEinstein`.
  * `info` is a boolean flag to enable/disable logging. Default is `true`.

Note that if `eig` is a diagonalized `Hamiltonian`, the `μ`, `N` and `statistics` parameters are inserted automatically.
