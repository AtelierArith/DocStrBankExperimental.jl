```
basis(elem::Pyr,N,r,s,t,tol=1e-12)
```

Computes orthonormal semi-nodal basis on the biunit pyramid element.

Warning: nodal derivative matrices may contain errors for nodes at t = 1. A way to avoid this is to use weak differentiation matrices computed using quadrature rules with only interior nodes.
