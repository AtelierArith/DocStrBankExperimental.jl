```
PerspectiveMap()
```

視点変換を構築します。視点変換は、例えば、3D空間の点を理想的なピンホールカメラの2D仮想スクリーンに「投影」します（カメラから1の距離にあります）。カメラは正のZ軸（または一般的には最終次元）に向けられており、カメラの前にある物体の`x`および`y`成分の符号は保持されます（カメラの後ろにある物体も投影され、したがって反転します - これらを必要に応じてカリングするのはユーザーの責任です）。

この変換は、カメラの位置と向きを定義する他の座標変換と組み合わせて使用するように設計されています。例えば：

```julia
cam_transform = PerspectiveMap() ∘ inv(AffineMap(cam_rotation, cam_position))
screen_points = map(cam_transform, points)
```

（参照：[`cameramap`](@ref)）
