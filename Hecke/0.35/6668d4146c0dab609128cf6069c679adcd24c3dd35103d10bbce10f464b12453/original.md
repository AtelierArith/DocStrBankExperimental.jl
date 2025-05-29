```
ray_class_group(m::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, inf_plc::Vector{InfPlc}; n_quo::Int, lp::Dict{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, Int}) -> FinGenAbGroup, MapRayClassGrp
```

Given an ideal $m$ and a set of infinite places of $K$, this function returns the corresponding ray class group as an abstract group $\mathcal {Cl}_m$ and a map going from the group into the group of ideals of $K$ that are coprime to $m$. If `n_quo` is set, it will return the group modulo `n_quo`. The factorization of $m$ can be given with the keyword argument `lp`.
