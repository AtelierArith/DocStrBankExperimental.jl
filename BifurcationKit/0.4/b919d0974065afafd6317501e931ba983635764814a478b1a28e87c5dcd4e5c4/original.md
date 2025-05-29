```
PrecPartialSchurArnoldiMethod(J, N, nev, which = LM(); tol = 1e-9, kwargs...)
```

Builds a preconditioner based on deflation of `nev` eigenvalues chosen according to `which`. A partial Schur decomposition is computed (Matrix-Free), using the package `ArnoldiMethod.jl`, from which a projection is built. See the package `ArnoldiMethod.jl` for how to pass the proper options.
