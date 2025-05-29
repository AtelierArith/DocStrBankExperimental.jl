```
truncate(::AbstractPolynomial{T};
    rtol::Real = Base.rtoldefault(real(T)), atol::Real = 0)
```

Rounds off coefficients close to zero, as determined by `rtol` and `atol`, and then chops any leading zeros. Returns a new polynomial.
