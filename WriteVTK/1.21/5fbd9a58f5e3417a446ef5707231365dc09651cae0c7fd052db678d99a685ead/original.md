```
Base.close(vtk::VTKFile) -> Vector{String}
```

Write and close VTK file.

Returns a list of paths pointing to the written VTK files (typically just one file, but can be more for e.g. `MultiblockFile`).

---

```
Base.close(vtm::MultiblockFile) -> Vector{String}
```

Save and close multiblock file (`.vtm`). The VTK files included in the multiblock file are also saved.
