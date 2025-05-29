```
unitary([T::Type=Float64,] codomain::TensorSpace, domain::TensorSpace) -> TensorMap
unitary([T::Type=Float64,] codomain ← domain) -> TensorMap
unitary([T::Type=Float64,] domain → codomain) -> TensorMap
unitary!(t::AbstractTensorMap) -> AbstractTensorMap
```

コドメインとドメインの間の特定のユニタリモルフィズムを構築します。すなわち、`scalartype(t) = T` が `T` が `Number` 型である場合、または `storagetype(t) = T` が `T` が `DenseVector` 型である場合の `t::TensorMap` を返します。空間が同型でない場合、または空間タイプがユークリッド内積を持たない場合、エラーがスローされます。

!!! note
    特定のユニタリに対する標準的な選択はありませんが、現在の選択は `unitary(cod, dom) == inv(unitary(dom, cod)) = adjoint(unitary(dom, cod))` であるようにしています。


[`isomorphism`](@ref) および [`isometry`](@ref) も参照してください。
