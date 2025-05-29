```
dos(eig[, E; broaden])
dos(gf[, E; broaden])
```

Calculates the DOS (density of states) for a given eigensystem at energy `E`. If `E` is not specified, a function that calculates the DOS at a given energy is returned.

## Arguments

  * `eig` is an `Eigensystem` or `HamiltonianEigensystem`.
  * `gf` is a `GreenFunction`.
  * `E` is the energy at which the DOS is calculated.

## Keyword arguments

  * `broaden` is the broadening factor for the energy levels, default is `0.1`.
