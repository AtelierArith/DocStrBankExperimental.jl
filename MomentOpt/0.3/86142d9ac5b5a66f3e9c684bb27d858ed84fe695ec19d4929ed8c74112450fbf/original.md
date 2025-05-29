```
 partial_integrate(p::MP.AbstractPolynomialLike, m::AbstractGMPMeasure)
```

Returns the integral of p with respect to m, in case m does not cover all variables of p. The result is a polynomial in the remaining variables.  
