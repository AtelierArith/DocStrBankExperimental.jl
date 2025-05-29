```
chebgradient(c::ChebPoly, x)
```

Return a tuple `(v, ∇v)` where `v` is the value `c(x)` of the Chebyshev polynomial `c` at `x`, and `∇v` is the gradient of this value with respect to `x`.

(Requires `c` to be a scalar-valued polynomial; if `c` is vector-valued, you should use `chebjacobian` instead.)

If `x` is a scalar, returns a scalar `∇v`, i.e. `(v, ∂v/∂x).
