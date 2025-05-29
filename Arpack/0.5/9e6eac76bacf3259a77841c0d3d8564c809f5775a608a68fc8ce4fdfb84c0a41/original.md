```
eigs(A, B; nev=6, ncv=max(20,2*nev+1), which=:LM, tol=0.0, maxiter=300, sigma=nothing, ritzvec=true, v0=zeros((0,)), check=0) -> (d,[v,],nconv,niter,nmult,resid)
```

Computes generalized eigenvalues `d` of `A` and `B` using implicitly restarted Lanczos or Arnoldi iterations for real symmetric or general nonsymmetric matrices respectively. See [the manual](@ref man-eigsgen) for more information.

When `check = 0`, an error is thrown if maximum number of iterations taken (`info = 1`). This usually means all possible eigenvalues has been found according to ARPACK manual. When `check = 1`, return currently converged eigenvalues when `info = 1`. And a `@warn` will given. When `check = 2`, return currently converged eigenvalues when `info = 1`.
