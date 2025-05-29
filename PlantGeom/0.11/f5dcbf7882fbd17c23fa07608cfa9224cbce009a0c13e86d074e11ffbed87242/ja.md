```
get_ref_meshes_color(meshes::Vector{RefMesh})
```

参照メッシュの色を取得します（現時点では拡散部分のみ）。

# 例

```julia
using MultiScaleTreeGraph, PlantGeom
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.opf")
opf = read_opf(file)
meshes = get_ref_meshes(opf)
PlantGeom.get_ref_meshes_color(meshes)
```
