```
hom(
  T::TorQuadModule,
  S::TorQuadModule,
  M::ZZMatrix;
  check::Bool=true,
) -> TorQuadModuleMap
```

Given two torsion quadratic modules `T` and `S`, and a matrix `M` defining an abelian group homomorphism between the underlying groups of `T` and `S`, return the corresponding abelian group homomorphism between `T` and `S`. If `check` is set to `true`, the function checks whether `M` defines a morphism of finite abelian groups between `T` and `S`.
