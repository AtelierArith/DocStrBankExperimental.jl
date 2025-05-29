```
RefMesh(
    name::S
    mesh::SimpleMesh
    normals::N
    texture_coords::T
    material::M
    taper::Bool
)

RefMesh(name, mesh, material = RGB(220 / 255, 220 / 255, 220 / 255))
```

RefMesh type. Stores all information about a Mesh:

  * `name::S`: the mesh name
  * `mesh::SimpleMesh`: the actual mesh information -> points and topology
  * `normals::Vector{Float64}`: the normals, given as a vector of x1,y1,z1,x2,y2,z2...
  * `texture_coords::Vector{Float64}`: the texture coordinates (not used yet), idem, a vector
  * `material::M`: the material, used to set the shading
  * `taper::Bool`: `true` if tapering is enabled

The reference meshes are then transformed on each node of the MTG using a transformation matrix to match the actual mesh.
