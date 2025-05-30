```
DirectionalSource(box::AABB; θ, Φ, radiosity, nrays)
DirectionalSource(mesh::Mesh; θ, Φ, radiosity, nrays)
```

軸に整列したバウンディングボックス（`box`）または`Mesh`オブジェクトを提供し、天頂角（`θ`）と方位角（`Φ`）、水平面に投影されたソースの放射率、および生成するレイの数を指定することで、方向性ソース（幾何学的および角度コンポーネントを含む）を作成します。方向性ソースは、メッシュを拡張するグリッドクローンがない場合に不正確な結果を生成する可能性があります。これは、レイがメッシュのバウンディングボックスの上面から生成されるためです。光源に関する詳細はVPLドキュメントを参照してください。

## 例

```jldoctest
julia> using PlantGeomPrimitives;

julia> mesh = Ellipse();

julia> source = DirectionalSource(mesh, θ = 0.0, Φ = 0.0, radiosity = 1.0, nrays = 1_000);
```
