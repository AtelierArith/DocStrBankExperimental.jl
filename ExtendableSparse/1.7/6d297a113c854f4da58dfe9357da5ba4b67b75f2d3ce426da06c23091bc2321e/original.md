```julia
fdrand!(A, nx; ...)
fdrand!(A, nx, ny; ...)
fdrand!(A, nx, ny, nz; update, rand)

```

After setting  all nonzero entries  to zero, fill resp.  update matrix with finite  difference discretization data  on a unit  hypercube. See [`fdrand`](@ref) for documentation of the parameters.

It is required that `size(A)==(N,N)` where `N=nx*ny*nz`
