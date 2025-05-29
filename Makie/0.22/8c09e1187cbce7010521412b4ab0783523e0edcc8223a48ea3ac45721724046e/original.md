```
zoom!(scene, cam::Camera3D, zoom_step[, cad = false, zoom_shift_lookat = false])
```

Zooms the camera in or out based on the multiplier `zoom_step`. A `zoom_step` of 1.0 is neutral, larger zooms out and lower zooms in.

If `cad = true` zooming will also apply a rotation based on how far the cursor is from the center of the scene. If `zoom_shift_lookat = true` and `projectiontype = Orthographic` zooming will keep the data under the cursor at the same screen space position.
