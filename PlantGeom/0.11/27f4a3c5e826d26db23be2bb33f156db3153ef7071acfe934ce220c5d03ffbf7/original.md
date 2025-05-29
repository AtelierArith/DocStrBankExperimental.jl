```
refmesh_to_mesh!(node)
refmesh_to_mesh(node)
```

Compute a node mesh based on the reference mesh, the transformation matrix and the tapering. The mutating version adds the new mesh to the `mesh` field of the geometry attribute of the node.

# Examples

```julia
using PlantGeom
file = joinpath(dirname(dirname(pathof(PlantGeom))),"test","files","simple_plant.opf")
opf = read_opf(file)

node = opf[1][1][1]

new_mesh = refmesh_to_mesh(node)

using GLMakie
viz(new_mesh)
```
