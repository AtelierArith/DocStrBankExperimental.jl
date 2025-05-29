```
inertia_subgroup(K::AbsSimpleNumField, P::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, m::Map) -> Grp, GrpToGrp
```

Given a prime ideal $P$ of a number field $K$ and a map `m` return from `automorphism_group(K)`, return the inertia subgroup of $P$ as a subgroup of the domain of `m`.
