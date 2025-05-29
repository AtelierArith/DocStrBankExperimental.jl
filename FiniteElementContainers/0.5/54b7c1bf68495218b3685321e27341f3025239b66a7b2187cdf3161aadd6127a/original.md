```julia
struct FileMesh{MeshObj} <: FiniteElementContainers.AbstractMesh
```

  * `file_name::String`
  * `mesh_obj::Any`

Mesh type that has a handle to an open mesh file object. This type's methods are "overridden" in extensions.

See FiniteElementContainersExodusExt for an example.
