```
struct SolidModel{T} where {T <: SolidModelKernel}
    name::String
    groups::NTuple{4,Dict{String,AbstractPhysicalGroup}}
end
SolidModel(name::String, kernel=OpenCascade; overwrite=false)
```

A 3D geometry model.

Geometry rendering, boolean operations, and export are provided by the specified `kernel`.

Physical groups can be accessed by name using indexing with a `String` or `Symbol` and a dimension: `mymodel["mygroup", 3]` will return the `PhysicalGroup` with dimension 3 called `mygroup`.

Physical groups can also be assigned as `mymodel["mygroup"] = dimtags`, where `dimtags` is a list of `NTuple{2, Int32}` of entities identified by `(dim, tag)` in `mymodel`. If `dimtags` includes entities of multiple dimensions, then a group is created for each dimension.

If the constructor is called with `overwrite=false` (the default), then an error will be thrown if a model with the same name already exists. If `overwrite=true`, then any existing model with the same name will be deleted and a new model will be created.

A `SolidModel` can be saved to a file with `FileIO.save(filename, sm)`. Supported filetypes for OpenCASCADE geometries are `.brep` and `.stp`. Meshes can be exported as `.msh2` (compatible with Palace) or `.msh` (most recent Gmsh format) files.
