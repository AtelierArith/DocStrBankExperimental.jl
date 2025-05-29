```
ray_class_field(m::Union{MapClassGrp, MapRayClassGrp}, quomap::FinGenAbGroupHom) -> ClassField
```

For $m$ a map computed by either {ray*class*group} or {class_group} and $q$ a canonical projection (quotient map) as returned by {quo} for q quotient of the domain of $m$ and a subgroup of $m$, create the (formal) abelian extension where the (relative) automorphism group is canonically isomorphic to the codomain of $q$.
