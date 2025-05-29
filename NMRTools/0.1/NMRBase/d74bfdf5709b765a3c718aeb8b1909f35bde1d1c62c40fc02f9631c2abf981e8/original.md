```
pcls(A, y)
```

Compute the phase-constrained least squares solution:

$$
y = A x e^{i\phi}
$$

following the algorithm of Bydder (2010) *Lin Alg & Apps*.

Returns the tuple `(x, ϕ)`, containing the component amplitudes and global phase.

If passed a matrix `Y`, the function will return a matrix of component amplitudes and a list of global phases corresponding to each row.

# Arguments

  * `A`: (m,n) complex matrix with component spectra
  * `y`: (m,) complex vector containing the observed spectrum
