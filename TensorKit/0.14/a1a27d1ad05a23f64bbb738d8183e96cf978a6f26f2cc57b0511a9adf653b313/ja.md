```
isomorphism([T::Type=Float64,] codomain::TensorSpace, domain::TensorSpace) -> TensorMap
isomorphism([T::Type=Float64,] codomain ← domain) -> TensorMap
isomorphism([T::Type=Float64,] domain → codomain) -> TensorMap
isomorphism!(t::AbstractTensorMap) -> AbstractTensorMap
```

コドメインとドメインの間の特定の同型を構築します。すなわち、`scalartype(t) = T` が `T` が `Number` 型である場合、または `storagetype(t) = T` が `T` が `DenseVector` 型である場合の `t::TensorMap` を返します。空間が同型でない場合、エラーがスローされます。

!!! note
    特定の同型に対する標準的な選択はありませんが、現在の選択は `isomorphism(cod, dom) == inv(isomorphism(dom, cod))` であることを考慮しています。


また、`InnerProductStyle(cod) === EuclideanInnerProduct()` の場合は [`unitary`](@ref) を参照してください。
