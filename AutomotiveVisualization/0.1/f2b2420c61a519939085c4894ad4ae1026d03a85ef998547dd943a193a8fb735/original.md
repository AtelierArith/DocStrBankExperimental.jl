```
ComposedCamera <: Camera
```

Composition of several cameras. The `update_camera` actions of the individual cameras are applied in the order in which they are saved in the `cameras` array. States of individual cameras are ignored, the state of the composed camera is the one that will be used for rendering.

Example Usage

```
cam = ComposedCamera(cameras=[SceneFollowCamera(), ZoomingCamera()])
```
