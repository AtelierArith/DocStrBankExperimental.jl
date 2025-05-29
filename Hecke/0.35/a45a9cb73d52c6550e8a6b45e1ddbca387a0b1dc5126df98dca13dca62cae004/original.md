```
ideal(A::AbstractAssociativeAlgebra, M::QQMatrix; M_in_hnf::Bool = false) -> AlgAssAbsOrdIdl
```

Returns the ideal in $A$ with basis matrix $M$. If `M_in_hnf == true`, it is assumed that $M$ is already in lower left HNF.
