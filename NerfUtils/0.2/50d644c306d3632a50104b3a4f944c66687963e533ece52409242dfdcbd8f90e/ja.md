```
Camera(projection, intrinsics::CameraIntrinsics)
```

Cameraは元の焦点距離を維持します。これは、モデルが特定の値で訓練されたため、元のアスペクトを保持したいからです。

# 引数:

  * `projection::MMatrix{3, 4, Float32}`: カメラから世界への投影。
  * `intrinsics::CameraIntrinsics`: カメラの内部パラメータ。
  * `original_focal::SVector{2, Float32}`: 元の焦点距離。カメラのリサイズ時に元の焦点距離のアスペクト比を保持するために使用されます。
  * `original_resolution::SVector{2, UInt32}`: 元の解像度。カメラのリサイズ時に`original_focal`に掛けるスケール値を計算するために使用されます。
