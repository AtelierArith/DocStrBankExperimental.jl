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

RefMesh型。メッシュに関するすべての情報を格納します：

  * `name::S`: メッシュ名
  * `mesh::SimpleMesh`: 実際のメッシュ情報 -> 点とトポロジー
  * `normals::Vector{Float64}`: 法線、x1,y1,z1,x2,y2,z2...のベクトルとして与えられます
  * `texture_coords::Vector{Float64}`: テクスチャ座標（まだ使用されていません）、同様にベクトル
  * `material::M`: マテリアル、シェーディングを設定するために使用されます
  * `taper::Bool`: テーパーが有効な場合は`true`

参照メッシュは、実際のメッシュに一致させるために変換行列を使用してMTGの各ノードで変換されます。
