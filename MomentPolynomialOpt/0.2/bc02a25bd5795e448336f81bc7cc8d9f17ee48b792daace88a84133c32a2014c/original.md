```julia
j = polar_ideal(f, [h1, h2, ...], [g1, g2, ...], X)
```

Compute generators of the polar ideal associated with `f, [h1, h2, ...], [g1, g2, ...]` (equality constraints hi == 0 and the sign constraints gi >= 0) with respect to the variable vector X.

f, hi, gi should be polynomials in variables X.
