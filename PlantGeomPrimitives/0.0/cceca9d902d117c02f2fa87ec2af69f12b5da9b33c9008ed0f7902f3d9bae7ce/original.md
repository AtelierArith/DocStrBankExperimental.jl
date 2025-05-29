```
save_mesh(mesh; fileformat = :STL_BINARY, filename)
```

Save a mesh into an external file using a variety of formats.

# Arguments

  * `mesh`: Object of type `Mesh`.
  * `fileformat`: Format to store the mesh as symbol.
  * `filename`: Name of the file in which to store the mesh as string.

# Details

The `fileformat` should take one of the following arguments: `:STL_BINARY`, `:STL_ASCII`, `:PLY_BINARY`, `:PLY_ASCII` or `:OBJ`. Note that these names should be passed as symnols.

# Example

```julia
julia> v = [Vec(0.0, 0.0, 0.0), Vec(0.0, 1.0, 0.0), Vec(1.0, 0.0, 0.0)];

julia> mesh = Mesh(v);

julia> save_mesh(mesh, fileformat = :STL_BINARY, filename = "path/to/mesh.bstl");
```
