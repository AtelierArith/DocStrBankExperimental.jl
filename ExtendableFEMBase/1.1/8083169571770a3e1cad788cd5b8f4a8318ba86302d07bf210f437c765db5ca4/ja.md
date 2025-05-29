```julia
get_ndofs_all(
    AT::Type{<:ExtendableGrids.AssemblyType},
    FEType::Type{<:ExtendableFEMBase.AbstractFiniteElement},
    EG::Type{<:ExtendableGrids.AbstractElementGeometry}
) -> Int64

```

は、指定された AssemblyType、FEType、およびジオメトリに対する自由度の合計数を返します。
