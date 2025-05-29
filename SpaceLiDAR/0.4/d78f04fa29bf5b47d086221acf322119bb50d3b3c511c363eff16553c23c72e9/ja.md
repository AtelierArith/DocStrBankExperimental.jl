```
shift(longitude, latitude, angle, distance)
```

`longitude` と `latitude` を `angle` の方向に [m] 単位で `distance` だけシフトします。北は 0° です。シフトされた座標のタプル `(longitude, latitude)` を返します。これは、[`angle`](@ref) と組み合わせて、SpaceLiDAR ポイントをトラックの左または右にオフセットするのに便利です。
