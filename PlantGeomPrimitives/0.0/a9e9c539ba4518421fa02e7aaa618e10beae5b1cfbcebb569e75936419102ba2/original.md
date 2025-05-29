```
load_mesh(filename, type = Float64)
```

Import a mesh from a file given by `filename`. Supported formats include stl, ply, obj and msh. By default, this will generate a `Mesh` object that uses double floating-point precision. However, a lower precision can be specified by passing the relevant data type as in `load_mesh(filename, Float32)`.

# Arguments

  * `filename`: The path to the file containing the mesh.
  * `type`: The floating-point precision type for the mesh data (default is `Float64`).

# Example

```julia
julia> mesh = load_mesh("path/to/mesh.obj");

julia> mesh = load_mesh("path/to/mesh.obj", Float32);
```
