```
ideal(A::AbstractAssociativeAlgebra, M::PMat; M_in_hnf::Bool = false) -> AlgAssRelOrdIdl
```

Returns the ideal in $A$ with basis pseudo-matrix $M$. If `M_in_hnf == true`, it is assumed that $M$ is already in lower left pseudo HNF.
