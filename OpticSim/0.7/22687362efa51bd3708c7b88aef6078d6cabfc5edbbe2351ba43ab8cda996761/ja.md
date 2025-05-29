```
ParaxialLens{T} <: Surface{T}
```

`surfacenormal` はレンズの**出力**方向です。パラキシアルレンズは二つの材料の間の界面として機能することができないため、デフォルトで空気が指定される単一の外部材料のみが指定されます。

以下の関数を使用して作成します。

```julia
ParaxialLensEllipse(focaldistance, halfsizeu, halfsizev, surfacenormal, centrepoint; rotationvec = [0.0, 1.0, 0.0], outsidematerial = AGFFileReader.Air, decenteruv = (0.0, 0.0))
ParaxialLensRect(focaldistance, halfsizeu, halfsizev, surfacenormal, centrepoint; rotationvec = [0.0, 1.0, 0.0], outsidematerial = AGFFileReader.Air, decenteruv = (0.0, 0.0))
ParaxialLensHex(focaldistance, side_length, surfacenormal, centrepoint; rotationvec = [0.0, 1.0, 0.0], outsidematerial = AGFFileReader.Air, decenteruv = (0.0, 0.0))
ParaxialLensConvexPoly(focaldistance, local_frame, local_polygon_points, local_center_point; outsidematerial = AGFFileReader.Air)
```
