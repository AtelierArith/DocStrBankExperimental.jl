```
clenshaw_curtis_rings(N, [T=Float64])
```

Values of the colatitude coordinate ($θ$) appropriate for quadrature by the Clenshaw-Curtis rule, using weights provided by [`clenshaw_curtis`](@ref).

Note that the first argument to this function is `N`, rather than the `ℓₘₐₓ` used in some other functions.  For spin-weighted spherical harmonics, you may want to use `N=2ℓₘₐₓ+1`.
