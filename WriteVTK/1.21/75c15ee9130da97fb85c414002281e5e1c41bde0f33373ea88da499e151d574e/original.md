```
multiblock_add_block(
    vtm::Union{MultiblockFile, VTKBlock},
    vtk::VTKFile,
    [name = ""],
) -> nothing
```

Add a block to a [`MultiblockFile`](@ref) or a [`VTKBlock`](@ref).

---

```
multiblock_add_block(
    vtm::Union{MultiblockFile, VTKBlock},
    [name = ""],
) -> VTKBlock
```

Create a sub-block in a [`MultiblockFile`](@ref) or a [`VTKBlock`](@ref).

Returns a new [`VTKBlock`](@ref).
