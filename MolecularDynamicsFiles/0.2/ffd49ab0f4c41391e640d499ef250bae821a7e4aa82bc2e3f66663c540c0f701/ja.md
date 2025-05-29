```julia
pbc(
    bc::MolecularDynamicsFiles.BoundaryConditions
) -> Tuple{Bool, Bool, Bool}

```

周期的境界条件を返します（各次元の境界スタイルが周期的である場合）。
