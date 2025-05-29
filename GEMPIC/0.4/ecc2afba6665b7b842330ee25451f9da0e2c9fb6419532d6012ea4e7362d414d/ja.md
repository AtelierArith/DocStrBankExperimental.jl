```
ThreeDGrid( dimx, nx, dimy, ny, dimz, nz)
```

立方体 `dimx` x `dimy` x `dimz` 上に `nx` x `ny` x `nz` ポイントの直交メッシュを生成します。

  * `nx` : インデックスは [1:nx] にあります
  * `ny` : インデックスは [1:ny] にあります
  * `nz` : インデックスは [1:nz] にあります
  * `dimx = xmax - xmin`
  * `dimy = ymax - ymin`
  * `dimz = zmax - zmin`
  * `x, y, z` : ノードの位置
  * `dx, dy, dz` : ステップサイズ
