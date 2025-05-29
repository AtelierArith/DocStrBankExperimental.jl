```
hom(
  T::TorQuadModule,
  S::TorQuadModule,
  A::Vector,
  B::Vector;
  check::Bool=true,
) -> TorQuadModuleMap
```

Given two torsion quadratic modules `T` and `S`, and two lists `A` and `B` of elements of `T` and `S` respectively, return the abelian group homomorphism between `T` and `S` mapping `A[i]` to `B[i]` for all i. If `check` is set to `true`, the function checks whether the inputs define a morphism of finite abelian groups.
