```
sensorsize(model::AbstractCameraModel)
```

カメラセンサーのサイズを返します。デフォルトでは、`columns(model)` と `rows(model)` を呼び出して SVector{2} を構築します。

`sensorsize(cameramodel::AbstractCameraModel) = SVector{2}(columns(cameramodel), rows(cameramodel))`
