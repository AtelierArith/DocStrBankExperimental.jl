```
hom(
  T::TorQuadModule,
  S::TorQuadModule,
  img::Vector;
  check::Bool=true
) -> TorQuadModuleMap
```

Given two torsion quadratic modules `T` and `S`, and a list `img` of elements of `S` containing as many elements as `ngens(T)`, return the abelian group homomorphism between `T` and `S` mapping the generators of `T` to the elements of `img`. If `check` is set to `true`, the function checks whether the inputs define a morphism of finite abelian groups.
