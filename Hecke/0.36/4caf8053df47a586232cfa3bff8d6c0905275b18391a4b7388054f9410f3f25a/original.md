```
ideal(A::AbstractAssociativeAlgebra, O::AlgAssAbsOrd, M::QQMatrix; side::Symbol = :nothing,
      M_in_hnf::Bool = false)
  -> AlgAssAbsOrdIdl
```

Returns the ideal of $O$ in $A$ with basis matrix $M$ (in the basis of $A$). If the ideal is known to be a right/left/twosided ideal of $O$, `side` may be set to `:right`/`:left`/`:twosided` respectively. If `M_in_hnf == true`, it is assumed that $M$ is already in lower left HNF.
