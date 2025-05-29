```
refmesh_to_mesh!(node)
refmesh_to_mesh(node)
```

参照メッシュ、変換行列、およびテーパーに基づいてノードメッシュを計算します。ミューテーションバージョンは、新しいメッシュをノードのジオメトリアトリビュートの `mesh` フィールドに追加します。

# 例

```julia
using PlantGeom
file = joinpath(dirname(dirname(pathof(PlantGeom))),"test","files","simple_plant.opf")
opf = read_opf(file)

node = opf[1][1][1]

new_mesh = refmesh_to_mesh(node)

using GLMakie
viz(new_mesh)
```
