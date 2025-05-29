```
multiblock_add_block(
    vtm::Union{MultiblockFile, VTKBlock},
    vtk::VTKFile,
    [name = ""],
) -> nothing
```

[`MultiblockFile`](@ref) または [`VTKBlock`](@ref) にブロックを追加します。

---

```
multiblock_add_block(
    vtm::Union{MultiblockFile, VTKBlock},
    [name = ""],
) -> VTKBlock
```

[`MultiblockFile`](@ref) または [`VTKBlock`](@ref) にサブブロックを作成します。

新しい [`VTKBlock`](@ref) を返します。
