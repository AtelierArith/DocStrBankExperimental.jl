```
IntegDomain{S<:AbstractFESet, F<:Function}
```

Integration domain.

  * `T` = type of finite element set.  The type of the FE set will be dependent upon the operations required. For instance, for interior (volume) integrals such as body load or the stiffness hexahedral H8 may be used, whereas for boundary  (surface) integrals quadrilateral Q4 would be needed.
  * `F` = type of function to return the "other" dimension.

An integration domain consists of the finite elements that approximate the geometry, the function to supply the "missing" (other) dimension, indication whether or not the integration domain represents an axially symmetric situation, and integration rule used to evaluate integrals over the domain.
