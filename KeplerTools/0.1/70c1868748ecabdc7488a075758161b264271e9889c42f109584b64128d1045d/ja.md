```
basis = basis_rotation(Ω, i, ω)
basis = basis_rotation(xvec, yvec)
basis_rotation() = one(RotMatrix{3, Float64})
```

RAAN `Ω`、傾斜角 `i`、および近点引数 `ω` から、軌道の周辺平面を慣性系に変換する回転行列を計算します。この行列では、最初の列は軌道の近点を指す単位ベクトルであり、第三の列は法線方向を指す単位ベクトルです。

2つのベクトル `xvec` と `yvec` が提供されると、2つのベクトルが定義する平面を記述する回転行列が構築され、`normalize(xvec)` が最初の基底ベクトルになります。
