```
eigs(A; nev=6, ncv=max(20,2*nev+1), which=:LM, tol=0.0, maxiter=300, sigma=nothing, ritzvec=true, explicittransform=:auto, v0=zeros((0,)), check=0) -> (d,[v,],nconv,niter,nmult,resid)
```

Computes eigenvalues `d` of `A` using implicitly restarted Lanczos or Arnoldi iterations for real symmetric or general nonsymmetric matrices respectively. See [the manual](@ref man-eigs) for more information.

`eigs` returns the `nev` requested eigenvalues in `d`, the corresponding Ritz vectors `v` (only if `ritzvec=true`), the number of converged eigenvalues `nconv`, the number of iterations `niter` and the number of matrix vector multiplications `nmult`, as well as the final residual vector `resid`. The parameter `explicittransform` takes the values `:auto`, `:none` or `:shiftinvert`, specifying if shift and invert should be explicitly invoked in julia code.

When `check = 0`, an error is thrown if maximum number of iterations taken (`info = 1`). This usually means all possible eigenvalues has been found according to ARPACK manual. When `check = 1`, return currently converged eigenvalues when `info = 1`. And a `@warn` will given. When `check = 2`, return currently converged eigenvalues when `info = 1`.

# Examples

```jldoctest
julia> using LinearAlgebra, Arpack

julia> A = Diagonal(1:4);

julia> λ, ϕ = eigs(A, nev = 2);

julia> λ
2-element Array{Float64,1}:
 3.9999999999999996
 3.000000000000001
```
