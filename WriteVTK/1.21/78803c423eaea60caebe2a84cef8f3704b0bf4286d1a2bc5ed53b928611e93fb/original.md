```
vtk_grid(vtm::Union{MultiblockFile, VTKBlock}, [filename], griddata...; kwargs...)
```

Create new dataset file that is added to an existent multiblock file. The VTK grid is specified by the elements of `griddata`.

If the filename is not given, it is determined automatically from the filename associated to `vtm` and the number of existent blocks.
