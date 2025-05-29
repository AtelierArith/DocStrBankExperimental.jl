```
chebjacobian(c::ChebPoly, x)
```

Return a tuple `(v, J)` where `v` is the value `c(x)` of the Chebyshev polynomial `c` at `x`, and `J` is the Jacobian of this value with respect to `x`.

That is, if `v` is a vector, then `J` is a matrix of `length(v)` × `length(x)` giving the derivatives of each component.  If `v` is a scalar, then `J` is a 1-row matrix; in this case you may wish to call `chebgradient` instead.
