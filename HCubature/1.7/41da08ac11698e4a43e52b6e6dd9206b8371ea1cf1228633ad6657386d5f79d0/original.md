```
hquadrature(f, a, b; norm=norm, rtol=sqrt(eps), atol=0, maxevals=typemax(Int), initdiv=1)
```

Compute the integral of f(x) from `a` to `b`.  The return value of `hcubature` is a tuple `(I, E)` of the estimated integral `I` and an estimated error `E`.

The other parameters are the same as [`hcubature`](@ref).  `hquadrature` is just a convenience wrapper around `hcubature` so that you can work with scalar `x`, `a`, and `b`, rather than 1-component vectors.

Alternatively, for 1d integrals you can import the [`QuadGK`](@ref) module and call the [`quadgk`](@ref) function, which provides additional flexibility e.g. in choosing the order of the quadrature rule.
