```
rand(M::ProductManifold; parts_kwargs = map(_ -> (;), M.manifolds))
```

[`ProductManifold`](@ref) `M` のランダムな点を返します。`parts_kwargs` は、`M.manifolds` の各多様体に対する `rand` のキーワード引数のタプルです。
