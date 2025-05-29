```
pvtk_grid(f::Function, args...; kwargs...)
```

Create VTK file and apply `f` to it. The file is automatically closed by the end of the call.

This allows to use the do-block syntax for creating VTK files:

```julia
saved_files = pvtk_grid(args...; kwargs...) do vtk
    # do stuff with the `vtk` file handler
end
```
