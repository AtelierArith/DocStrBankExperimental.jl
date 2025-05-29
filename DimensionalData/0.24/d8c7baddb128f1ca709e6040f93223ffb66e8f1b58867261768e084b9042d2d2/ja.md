```
DimTable <: AbstractDimTable

DimTable(A::AbstractDimArray)
```

`AbstractDimArray`からTables.jl/TableTraits.jl互換のオブジェクトを構築します。

このテーブルには、配列データのための列と、各`Dimension`インデックスのための列があり、[`DimColumn`]として表されます。これらは遅延生成され、必要に応じて生成されます。

列名は、次元タイプから[`DimensionalData.dim2key`](@ref)を使用して変換されます。これは、タイプ`Ti`が列名`:Ti`になり、`Dim{:custom}`が`:custom`になることを意味します。

次元列を取得するには、`Dimension`（`X()`）または`Dimension`タイプ（`X`）でインデックスを付けることができ、通常の`Int`または`Symbol`でもインデックスを付けることができます。
