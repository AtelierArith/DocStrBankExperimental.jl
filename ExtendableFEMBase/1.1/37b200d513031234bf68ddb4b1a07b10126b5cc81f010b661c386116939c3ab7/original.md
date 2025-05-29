```julia
EffAT4AssemblyType(
    _::Type{ON_CELLS},
    _::Type{ON_CELLS}
) -> Type{ON_CELLS}

```

Effective AssemblyType (on the subgrid) for two AssemblyTypes where the first one is related to where the finite element functions live and the second one to where something should be assembled both with respect to the common parent grid (e.g. face-based finite elements live on a subgrid of all faces, where the faces are the cells in this subgrid, and they cannot be evaluated over the cells of the parentgrid, but on the faces of the parengrid, which are the cells in the subgrid)
