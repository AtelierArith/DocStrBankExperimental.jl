```
get_ref_meshes_color(meshes::Vector{RefMesh})
```

Get the reference meshes colors (only the diffuse part for now).

# Examples

```julia
using MultiScaleTreeGraph, PlantGeom
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.opf")
opf = read_opf(file)
meshes = get_ref_meshes(opf)
PlantGeom.get_ref_meshes_color(meshes)
```
