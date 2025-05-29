```
PrecPartialSchurKrylovKit(J, x0, nev, which = :LM; krylovdim = max(2nev, 20), verbosity = 0)
```

Builds a preconditioner based on deflation of `nev` eigenvalues chosen according to `which`. A partial Schur decomposition is computed (Matrix-Free), using the package `KrylovKit.jl`, from which a projection is built. The options are similar to the ones of `EigKrylovKit()`.
