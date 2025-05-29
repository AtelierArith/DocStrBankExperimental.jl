```julia
Dofmap4AssemblyType(
    FES::ExtendableFEMBase.FESpace,
    AT::Type{<:ExtendableGrids.AssemblyType}
) -> Any

```

は、与えられたAssemblyTypeに対するFESpaceの対応するdofmapを生成します（FESpaceの（親）グリッドに関して仮定されています）。
