```
get_ref_meshes(mtg)
```

Get all reference meshes from an mtg, usually from an OPF.

# Examples

```julia
using PlantGeom
file = joinpath(dirname(dirname(pathof(PlantGeom))),"test","files","simple_plant.opf")
opf = read_opf(file)
meshes = get_ref_meshes(opf)

using GLMakie
viz(meshes)
```
