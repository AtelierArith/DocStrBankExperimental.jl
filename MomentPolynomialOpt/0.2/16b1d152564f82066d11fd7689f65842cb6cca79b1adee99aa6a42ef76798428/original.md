```julia
v, M = polar_minimize(f, [h1, h2, ...], [g1, g2, ...], X, degree_approx, optimizer)
```

Compute the infimum of the f (equality constraints hi == 0 and the sign constraints gi >= 0) on the moment side. It does that calling minimize(...), replacing the equality constraints  [h1, h2, ...] with generators of the polar ideal.

f, hi, gi should be polynomials in the variables X.

If the problem is feasible and has minimizers, it outputs

  * v: the minimum value
  * M: the moment model of type MOM.Model
