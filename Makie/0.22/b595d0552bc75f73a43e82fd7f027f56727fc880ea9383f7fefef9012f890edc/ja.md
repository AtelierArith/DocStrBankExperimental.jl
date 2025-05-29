```
update_cam!(scene, cam::Camera3D, ϕ, θ[, radius])
```

カメラの位置を、2つの角度 `0 ≤ ϕ ≤ 2π` と `-pi/2 ≤ θ ≤ pi/2` に基づいて設定し、現在の `cam.lookat[]` の周りのオプションの半径を指定します。
