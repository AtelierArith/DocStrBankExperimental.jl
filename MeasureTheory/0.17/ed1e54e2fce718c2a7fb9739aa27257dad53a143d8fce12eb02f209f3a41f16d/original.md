```
LKJCholesky(k=3, η=1.0)
LKJCholesky(k=3, logη=0.0)
```

`LKJCholesky(k, ...)` gives the `k×k` LKJ distribution (Lewandowski et al 2009) expressed as a Cholesky decomposition. As a special case, for `C = rand(LKJCholesky(k=K, η=1.0))` (or equivalently `C=rand(LKJCholesky{k}(k=K, logη=0.0))`), `C.L * C.U` is uniform over the set of all `K×K` correlation matrices. Note, however, that in this case `C.L` and `C.U` are **not** sampled uniformly (because the multiplication is nonlinear).

The `logdensity` method for this measure applies for `LowerTriangular`, `UpperTriangular`, or `Diagonal` matrices, and will "do the right thing". The `logdensity` **does not check if `L*U` yields a valid correlation matrix**.

Valid values are $η > 0$. When $η > 1$, the distribution is unimodal with a peak at `I`, while $0 < η < 1$ yields a trough. $η = 2$ is recommended as a vague prior.

Adapted from https://github.com/tpapp/AltDistributions.jl
