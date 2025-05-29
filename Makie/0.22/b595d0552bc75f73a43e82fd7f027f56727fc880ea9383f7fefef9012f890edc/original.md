```
update_cam!(scene, cam::Camera3D, ϕ, θ[, radius])
```

Set the camera position based on two angles `0 ≤ ϕ ≤ 2π` and `-pi/2 ≤ θ ≤ pi/2` and an optional radius around the current `cam.lookat[]`.
