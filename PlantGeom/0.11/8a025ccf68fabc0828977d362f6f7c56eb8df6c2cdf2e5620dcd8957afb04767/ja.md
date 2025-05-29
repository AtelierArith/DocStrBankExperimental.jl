```
transform_mesh!(node::Node, transformation)
```

ノードのジオメトリ `transformation` フィールドに新しい変換を追加します。変換は、以前の変換と合成されます（もしあれば）。

`transformation` は関数でなければなりません。

`Meshes.jl` の `revert` を使用して変換を反転させることも可能です。

# 例

```julia
using PlantGeom, MultiScaleTreeGraph, GLMakie, Rotations, Meshes

file = joinpath(dirname(dirname(pathof(PlantGeom))), "test", "files", "simple_plant.opf")
opf = read_opf(file)

# メッシュをそのまま可視化:
viz(opf)

# OPFをコピーし、全体の植物をy方向に15だけ移動させる（これはcm単位で、メッシュはXPloから来ています）:
opf2 = deepcopy(opf)
transform!(opf2, x -> transform_mesh!(x, Translate(0, 15, 0)))
viz!(opf2) # 同じ図で再度可視化

# 同様ですが、全体の植物をX軸の周りに回転させます:
opf3 = deepcopy(opf)
transform!(opf3, x -> transform_mesh!(x, Rotate(RotX(0.3))))
# NB: ここではRotations.jlのRotXを使用しています。入力はラジアンで、必要に応じてrad2degとdeg2radを使用してください。
viz!(opf3)

# 同様ですが、2番目の葉だけをZ軸の周りに回転させます:
opf4 = deepcopy(opf)
# 親の座標が必要なため、参照メッシュからメッシュを構築します:
transform!(opf4, refmesh_to_mesh!)

# OPFから2番目の葉を取得:
leaf_node = get_node(opf4, 8)

# 親ノード（内部ノード）のZ座標を取得:
parent_zmax = zmax(leaf_node.parent)

# 親ノードの最大Zによって定義されたZ軸の周りのメッシュの回転を定義:
transformation = recenter(Rotate(RotZ(1.0)), Point(0.0, 0.0, parent_zmax))

# 葉の変換行列とそのメッシュを更新:
transform_mesh!(leaf_node, transformation)

# 結果をプロット:
viz(opf)
viz!(opf4)
```
