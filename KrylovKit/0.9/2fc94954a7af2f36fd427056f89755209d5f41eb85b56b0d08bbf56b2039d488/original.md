```
GolubYe(; krylovdim=KrylovDefaults.krylovdim[],
        maxiter=KrylovDefaults.maxiter[],
        tol=KrylovDefaults.tol[],
        orth=KrylovDefaults.orth,
        eager=false,
        verbosity=KrylovDefaults.verbosity[])
```

Represents the Golub-Ye algorithm for solving hermitian (symmetric) generalized eigenvalue problems `A x = λ B x` with positive definite `B`, without the need for inverting `B`. Builds a Krylov subspace of size `krylovdim` starting from an estimate `x` by acting with `(A - ρ(x) B)`, where `ρ(x) = dot(x, A*x)/dot(x, B*x)`, and employing the Lanczos algorithm. This process is repeated at most `maxiter` times. In every iteration `k>1`, the subspace will also be expanded to size `krylovdim+1` by adding $x_k - x_{k-1}$, which is known as the LOPCG correction and was suggested by Money and Ye. With `krylovdim=2`, this algorithm becomes equivalent to `LOPCG`.
