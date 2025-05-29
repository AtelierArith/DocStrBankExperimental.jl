```
duallagrangecxd0(mesh, jct) -> basis
```

Build dual Lagrange piecewise constant elements. Boundary nodes are only considered if they are in the interior of `jct`.

The default dual function (`interpolatory=false`) is similar to the one depicted in Figure 3 of  Buffa et al (doi: 10.1090/S0025-5718-07-01965-5), with the difference that each individual shape function is normalized with respect to  the area so that overall the integral over the dual function is one.

When `interpolatory=true` is used, the function value is one on the support, and thus, it gives rise to a partition of unity.
