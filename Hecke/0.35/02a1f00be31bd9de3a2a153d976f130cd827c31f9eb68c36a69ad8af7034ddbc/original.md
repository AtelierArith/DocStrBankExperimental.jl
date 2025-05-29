```
hom(
  G::FinGenAbGroup,
  H::FinGenAbGroup,
  B::Vector;
  check::Bool=true,
) -> FinGenAbGroupHom
```

Return the group homomorphism $G\to H$ that sends `G[i]` to `B[i]` for all `i`. If `check` is set to `true`, the function checks whether the inputs indeed define a morphism of finitely generated abelian groups.
