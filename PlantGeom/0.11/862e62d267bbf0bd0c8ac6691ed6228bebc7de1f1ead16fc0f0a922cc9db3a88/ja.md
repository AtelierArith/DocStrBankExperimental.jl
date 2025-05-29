```
get_ref_meshes(mtg)
```

MTGからすべての参照メッシュを取得します。通常はOPFからです。

# 例

```julia
using PlantGeom
file = joinpath(dirname(dirname(pathof(PlantGeom))),"test","files","simple_plant.opf")
opf = read_opf(file)
meshes = get_ref_meshes(opf)

using GLMakie
viz(meshes)
```
