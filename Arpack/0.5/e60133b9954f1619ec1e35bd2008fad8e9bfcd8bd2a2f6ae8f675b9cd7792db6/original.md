```
svds(A; nsv=6, ritzvec=true, tol=0.0, maxiter=1000, ncv=2*nsv, v0=zeros((0,))) -> (SVD([left_sv,] s, [right_sv,]), nconv, niter, nmult, resid, check=0)
```

Computes the largest singular values `s` of `A` using implicitly restarted Lanczos iterations derived from [`eigs`](@ref). See [the manual](@ref man-svds) for more information.

When `check = 0`, an error is thrown if maximum number of iterations taken (`info = 1`). This usually means all possible eigenvalues has been found according to ARPACK manual. When `check = 1`, return currently converged eigenvalues when `info = 1`. And a `@warn` will given. When `check = 2`, return currently converged eigenvalues when `info = 1`.
