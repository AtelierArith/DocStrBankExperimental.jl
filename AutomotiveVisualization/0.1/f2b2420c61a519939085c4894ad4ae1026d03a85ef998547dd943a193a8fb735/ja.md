```
ComposedCamera <: Camera
```

複数のカメラの合成。個々のカメラの `update_camera` アクションは、`cameras` 配列に保存されている順序で適用されます。個々のカメラの状態は無視され、合成カメラの状態がレンダリングに使用されるものとなります。

使用例

```
cam = ComposedCamera(cameras=[SceneFollowCamera(), ZoomingCamera()])
```
