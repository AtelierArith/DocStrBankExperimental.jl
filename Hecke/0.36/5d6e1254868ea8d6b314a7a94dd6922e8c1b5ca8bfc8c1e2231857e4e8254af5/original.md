```
hom(
  G::FinGenAbGroup,
  H::FinGenAbGroup,
  M::ZZMatrix;
  check::Bool=true,
) -> FinGenAbGroupHom
```

Return the group homomorphism $G\to H$ defined by the integer matrix $M = (m_{ij})$, by sending the $i$th generator of $G$ to $\sum_{j=1}^nm_{ij}h_j$ where $h_1,\ldots, h_n$ are the generators of $H$. If `check` is set to `true`, the function checks whether `M` indeed defines a morphism of finitely generated abelian groups.
