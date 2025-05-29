```
get_chevyshevs_up_to(N::Integer, first_kind::Bool = true)
```

Get the first N chebyshev polynomials returned as a vector of `UnivariateFunction`s. The first 20 polynomials of each are precompiled into the binaries for speed. If you need more than that they will be calculated at runtime.

These can be from either the first kind or second kind polynomial sequence.

### Inputs

  * `N` - How many chebyshev polynomials do you want.
  * `first_kind` - A Bool. If true you get first kind polynomials. If false you get second kind.

### Returns

  * A `Vector` of `UnivariateFunction`s for each polynomial.
