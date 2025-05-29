```
basis_overlap(A::FEDVROrRestricted, B)
```

Transforming to FEDVR is much the same as for finite-differences; evaluate at the quadrature nodes and scale by the weights. However, this has to be done per-element, so we feed it through the interpolation routines already setup for this.
