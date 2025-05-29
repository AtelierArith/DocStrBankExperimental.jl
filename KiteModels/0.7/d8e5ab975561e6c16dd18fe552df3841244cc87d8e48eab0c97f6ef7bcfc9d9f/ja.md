```
calculate_rotational_inertia!(s::AKM, include_kcu::Bool=true, around_kcu::Bool=false)
```

設定から凧モデルの回転慣性 (Ixx, Ixy, Ixz, Iyy, Iyz, Izz) を計算します。質量を初期化することで凧モデルを修正します。

パラメータ:

  * X: 点質量のx座標。
  * Y: 点質量のy座標。
  * Z: 点質量のz座標。
  * M: 点質量の質量。
  * `include_kcu`: 回転慣性計算にkcuを含めますか？
  * `around_kcu`: kcuを回転点として使用します。

戻り値:   タプル Ixx, Ixy, Ixz, Iyy, Iyz, Izz で、次のようになります:

  * Ixx: x軸周りの回転慣性。
  * Ixy: xy平面周りの回転慣性。
  * Ixz: xz平面周りの回転慣性。
  * Iyy: y軸周りの回転慣性。
  * Iyz: yz平面周りの回転慣性。
  * Izz: z軸周りの回転慣性。
