```
rotmat = orientation_rotation(pos, vel)
rotmat = orientation_rotation(θ, orb)
```

軌道状態ベクトル `pos`, `vel` のための順行、半径、法線方向を定義する回転行列を計算します。

真異常 `θ` と軌道 `orb` が提供される場合、それらは状態ベクトルを計算するために使用され、回転行列を計算するために使用されます。
