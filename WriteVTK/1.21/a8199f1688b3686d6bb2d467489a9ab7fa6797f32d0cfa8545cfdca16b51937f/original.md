```
vtk_multiblock(f::Function, args...; kwargs...)
```

Create VTK file and apply `f` to it. The file is automatically closed by the end of the call.

This allows to use the do-block syntax for creating VTK files:

```julia
saved_files = vtk_multiblock(args...; kwargs...) do vtk
    # do stuff with the `vtk` file handler
end
```
