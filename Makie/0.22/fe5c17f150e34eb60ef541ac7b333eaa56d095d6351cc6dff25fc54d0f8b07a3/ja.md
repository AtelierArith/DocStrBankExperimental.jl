```
Camera(pixel_area)
```

関連するすべての行列と追加のパラメータを保持する構造体で、バックエンドがカメラベースの変換を適用できるようにします。

## フィールド

  * `pixel_space::Observables.Observable{StaticArraysCore.SMatrix{4, 4, Float64, 16}}`: ピクセルをデバイス単位に変換するために使用される投影
  * `view::Observables.Observable{StaticArraysCore.SMatrix{4, 4, Float64, 16}}`: ビューマトリックスは通常、シーンを回転、スケール、移動するために使用されます
  * `projection::Observables.Observable{StaticArraysCore.SMatrix{4, 4, Float64, 16}}`: 投影マトリックスは任意の透視変換に使用されます
  * `projectionview::Observables.Observable{StaticArraysCore.SMatrix{4, 4, Float64, 16}}`: 単に投影 * ビュー
  * `resolution::Observables.Observable{GeometryBasics.Vec{2, Float32}}`: このカメラが描画するキャンバスの解像度
  * `view_direction::Observables.Observable{GeometryBasics.Vec{3, Float32}}`: カメラが向いている方向。
  * `eyeposition::Observables.Observable{GeometryBasics.Vec{3, Float32}}`: レイトレーシングなどに使用されるカメラの目の位置。
  * `upvector::Observables.Observable{GeometryBasics.Vec{3, Float32}}`: 現在のカメラの上方向（例：2Dの場合はVec3f(0, 1, 0)）
  * `steering_nodes::Vector{Observables.ObserverFunction}`: カメラをインタラクティブにするために、ステアリングオブザーバブルが異なる行列に接続されます。これらを追跡する必要があるため、接続および切断できるようにします。
  * `calculated_values::Dict{Symbol, Observables.Observable}`
