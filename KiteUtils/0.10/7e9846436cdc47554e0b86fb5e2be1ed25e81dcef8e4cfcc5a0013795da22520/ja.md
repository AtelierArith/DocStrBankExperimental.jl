```
calculate_rotational_inertia(X::Vector, Y::Vector, Z::Vector, M::Vector,  
      around_center_of_mass::Bool=true, rotation_point::Vector=[0, 0, 0])
```

点質量の集合の回転慣性 (Ixx, Ixy, Ixz, Iyy, Iyz, Izz) を点の周りで計算します。デフォルトでは、この点は質量中心で計算されますが、rotation_point に任意の点を指定することができます。

パラメータ:

  * X: 点質量の x 座標。
  * Y: 点質量の y 座標。
  * Z: 点質量の z 座標。
  * M: 点質量の質量。
  * `around_center_of_mass`: 質量中心の周りで回転慣性を計算しますか？
  * `rotation_point`: 質量中心の周りで回転しない場合に使用される回転点。

戻り値: タプル Ixx, Ixy, Ixz, Iyy, Iyz, Izz で、次のようになります。

  * Ixx: x 軸周りの回転慣性。
  * Ixy: xy 平面周りの回転慣性。
  * Ixz: xz 平面周りの回転慣性。
  * Iyy: y 軸周りの回転慣性。
  * Iyz: yz 平面周りの回転慣性。
  * Izz: z 軸周りの回転慣性。
