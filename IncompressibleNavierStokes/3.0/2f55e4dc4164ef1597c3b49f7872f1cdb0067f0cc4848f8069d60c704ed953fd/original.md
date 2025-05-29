```julia
vtk_writer(; setup, nupdate, dir, filename, kwargs...)

```

Create processor that writes the solution every `nupdate` time steps to a VTK file. The resulting Paraview data collection file is stored in `"$dir/$filename.pvd"`. The `kwargs` are passed to [`snapshotsaver`](@ref).
