```julia
abstract type DofMap <: ExtendableGrids.AbstractGridAdjacency
```

Dofmaps are stored as an ExtendableGrids.AbstractGridAdjacency in the finite element space and collect information with respect to different AssemblyTypes. They are generated automatically on demand and the dofmaps associated to each subtype can be accessed via FESpace[DofMap].
