```
make_paraview_collection(; dir=pwd(), pvd_name=nothing, files=nothing, file_extension = ".vts", time = nothing)
```

In case one has a list of `*.vtk` files, this routine creates a `*.pvd` file that can be opened in Paraview. This is useful if you previously saved vtk files but didnt save it as a collection in the code itself.

# Optional options

  * `dir`:    directory where the `*.vtk` are stored.
  * `pvd_name`:  filename of the resulting `*.pvd` file without extension; if not specified, `full_simulation` is used.
  * `files`:  Vector of the `*.vtk` files without extension; if not specified, all `*.vtk` files in the directory are used.
  * `file_extension`:  file extension of the vtk files. Default is `.vts` but all `vt*` work.
  * `time`:  Vector of the timesteps; if not specified, pseudo time steps are assigned.
