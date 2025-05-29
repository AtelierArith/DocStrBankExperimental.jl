```
vtk_multiblock([f::Function], filename) -> MultiblockFile
```

Initialise VTK multiblock file, linking multiple VTK dataset files.

Returns a handler for a multiblock file. To recursively save the multiblock file and linked dataset files, call [`close`](@ref) on the returned handler.

Note that `close` is implicitly called if the optional `f` argument is passed. This is in particular what happens when using the do-block syntax.
