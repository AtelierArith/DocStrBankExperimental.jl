```
greenfunction(psi0, hamp, hamm[; E₀, tol, showprogress, kw...])
```

Calculates the Green's function for a many-body system with a given initial state `psi0`.

## Arguments

  * `psi0` is the initial state.
  * `hamp` is the Hamiltonian for the subspace with one more particle than in `psi0`.
  * `hamm` is the Hamiltonian for the subspace with one less particle than in `psi0`.

## Keyword arguments

  * `E₀` is the energy shift for the Green's function. Default is `0`. Use `E0` as a synonym   if Unicode input is not available.
  * `tol` is the tolerance for the new eigenvectors. Default is `1e-5`.
  * `showprogress` is a flag to show the progress bar. Default is `true`.

All other keyword arguments are passed to the `diagonalize` function. See its documentation for details.
