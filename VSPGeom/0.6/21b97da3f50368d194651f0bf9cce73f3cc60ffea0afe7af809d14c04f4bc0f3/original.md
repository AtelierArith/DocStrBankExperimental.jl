```
getVTKElements(mesh::TriMesh)
```

Convenience function that returns the datastructures `points` and `cells` required to write to a VTK file using the WriteVTK package. The user may write out a VTK file using,

```
WriteVTK.vtk_grid(filename, points, cells) do vtk
end
```

**Arguments**

  * `mesh::TriMesh`: [`TriMesh`](@ref) object

**Returns**

  * `points::Array{Float64}`: Array of coordinates in the STL mesh
  * `mesh::Array{meshCell}`: Array of MeshCell objects that WriteVTK uses
