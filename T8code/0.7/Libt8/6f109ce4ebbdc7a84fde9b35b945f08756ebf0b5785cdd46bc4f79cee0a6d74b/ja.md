```
t8_plane_point_inside(point_on_face, face_normal, point)
```

平面の内側に点があるかどうかを確認します。平面は点と面の法線によって記述されます。

# 引数

  * `point_on_face`:[in] 平面上の点
  * `face_normal`:[in] 面の法線
  * `point`:[in] チェックする点

# 戻り値

点が外側にある場合は0、そうでない場合は1を返します。

### プロトタイプ

```c
int t8_plane_point_inside (const double point_on_face[3], const double face_normal[3], const double point[3]);
```
