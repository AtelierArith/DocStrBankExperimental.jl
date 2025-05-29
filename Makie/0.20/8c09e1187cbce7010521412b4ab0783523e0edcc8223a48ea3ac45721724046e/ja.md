```
zoom!(scene, cam::Camera3D, zoom_step[, cad = false, zoom_shift_lookat = false])
```

カメラをズームインまたはズームアウトします。倍率 `zoom_step` に基づいています。`zoom_step` が 1.0 の場合は中立で、値が大きいほどズームアウトし、値が小さいほどズームインします。

`cad = true` の場合、ズーム時にカーソルがシーンの中心からどれだけ離れているかに基づいて回転も適用されます。`zoom_shift_lookat = true` かつ `projectiontype = Orthographic` の場合、ズーム時にカーソルの下のデータが同じ画面空間位置に保たれます。
