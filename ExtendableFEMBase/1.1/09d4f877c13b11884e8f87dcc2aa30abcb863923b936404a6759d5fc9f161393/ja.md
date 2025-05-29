```julia
get_ndofs(
    AT::Type{<:ExtendableGrids.AssemblyType},
    FEType::Type{<:ExtendableFEMBase.AbstractFiniteElement},
    EG::Type{<:ExtendableGrids.AbstractElementGeometry}
) -> Any

```

は、指定された AssemblyType、FEType、およびジオメトリに対する自由度の数を返します。
