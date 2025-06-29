```
norm_group(f::Nemo.PolyRingElem, mR::Hecke.MapRayClassGrp, is_abelian::Bool = true; of_closure::Bool = false) -> Hecke.FinGenGrpAb, Hecke.FinGenGrpAbMap

norm_group(f::Array{PolyRingElem{AbsSimpleNumFieldElem}}, mR::Hecke.MapRayClassGrp, is_abelian::Bool = true; of_closure::Bool = false) -> Hecke.FinGenGrpAb, Hecke.FinGenGrpAbMap
```

Computes the subgroup of the Ray Class Group $R$ given by the norm of the extension generated by a/the roots of $f$. If `is_abelian` is set to true, then the code assumes the field to be abelian, hence the algorithm stops when the quotient by the norm group has the correct order. Even though the algorithm is probabilistic by nature, in this case the result is guaranteed. If `of_closure` is given, then the norm group of the splitting field of the polynomial(s) is computed. It is the callers responsibility to ensure that the ray class group passed in is large enough.
