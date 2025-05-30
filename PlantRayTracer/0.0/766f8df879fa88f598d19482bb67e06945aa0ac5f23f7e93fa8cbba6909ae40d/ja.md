```
accelerate(mesh::Mesh; settings = RTSettings(), acceleration = Naive, rule = nothing)
```

メッシュ、設定、および加速関数から `AccMesh` オブジェクトを作成します（`Naive` または `BVH` から選択）。引数 `rule` は加速器 `BVH` のみで必要であり、`SAH` または `AvgSplit` 型のオブジェクトでなければなりません（`Naive` 加速器の場合は無視されます）。`AccMesh` オブジェクトには、元の 3D メッシュ `mesh` の上に構築された加速構造とグリッドクローン構造が含まれています。詳細については VPL ドキュメントを参照してください。

## 例

```jldoctest
julia> using PlantGeomPrimitives;

julia> mesh = Ellipse();

julia> acc = accelerate(mesh);
```
