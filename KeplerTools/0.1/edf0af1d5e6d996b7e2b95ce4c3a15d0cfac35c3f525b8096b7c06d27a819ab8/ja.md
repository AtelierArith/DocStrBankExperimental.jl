```
Δθ = angle_in_plane(vec, mat)
Δθ = angle_in_plane(vec1, vec2, mat)
Δθ = angle_in_plane(vec, orbit)
Δθ = angle_in_plane(vec, vec, orbit)
Δθ = angle_in_plane(vec, orbit, t)
Δθ = angle_in_plane(orbit1, orbit2, t)
```

2つのベクトルの間の角度を、軌道の基底行列 `mat` で定義された軌道平面に投影した後に計算します。

1つのベクトルのみが提供された場合、ベクトル `vec` と軌道の近点の間の角度が求められます。

ベクトル、軌道、および時間 `t` が提供された場合、ベクトルと軌道の位置の間の平面内の角度が `t` で求められます。

2つの軌道と時間 `t` が提供された場合、時間 `t` における2つの軌道の位置の間の平面内の角度が求められます。
