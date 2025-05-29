```
factorize!(mumps)
```

Factorize the matrix registered with the `Mumps` instance. The matrix must have been previously registered with `associate_matrix()`. After the factorization, the determinant, if requested, is stored in `mumps.det`. The MUMPS error code is stored in `mumps.err`.
