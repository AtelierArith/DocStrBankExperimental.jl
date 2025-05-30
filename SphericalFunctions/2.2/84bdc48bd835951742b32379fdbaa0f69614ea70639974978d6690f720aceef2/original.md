```
fejer2_rings(N, [T=Float64])
```

Values of the colatitude coordinate ($θ$) appropriate for quadrature by Fejér's second rule, using weights provided by [`fejer2`](@ref).

Note that the first argument to this function is `N`, rather than the `ℓₘₐₓ` used in some other functions.  For spin-weighted spherical harmonics, you may want to use `N=2ℓₘₐₓ+1`.
