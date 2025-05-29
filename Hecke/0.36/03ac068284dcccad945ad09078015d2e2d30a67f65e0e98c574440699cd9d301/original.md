```
hom(
  G::FinGenAbGroup,
  H::FinGenAbGroup,
  M::ZZMatrix,
  Minv::ZZMatrix;
  check::Bool=true,
) -> FinGenAbGroupHom
```

Return the group homomorphism $G\to H$ defined by the integer matrix $M = (m_{ij})$ (by sending the $i$th generator of $G$ to $\sum_{j=1}^nm_{ij}h_j$ where $h_1,\ldots, h_n$ are the generators of $H$) and with pseudo-inverse $H\to G$ (or right inverse) defined by `Minv`. If `check` is set to `true`, the function checks whether `M` and `Minv` indeed define morphisms of finitely generated abelian groups, and whether `Minv` defines a right inverse to `M`.
