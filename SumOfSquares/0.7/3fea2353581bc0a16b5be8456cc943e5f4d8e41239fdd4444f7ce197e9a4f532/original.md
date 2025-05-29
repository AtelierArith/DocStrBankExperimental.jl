```
struct ConvexPolyInnerCone{MCT} <: PolyJuMP.PolynomialSet end
```

Inner approximation of the set of convex polynomials defined by the set of polynomials such that their hessian belongs to to the set `PSDMatrixInnerCone{MCT}()`
