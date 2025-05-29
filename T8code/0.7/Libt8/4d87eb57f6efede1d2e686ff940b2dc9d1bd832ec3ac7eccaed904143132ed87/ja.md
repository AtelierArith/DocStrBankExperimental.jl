```
t8_geom_get_tet_face_intersection(face_index, ref_coords, face_intersection)
```

テトラヘドロンの面の交差点を計算します。これは、参照座標とその面の反対の頂点を通る光線の交差点です。面の交差点の座標は参照座標: [0,1]^3 です。

# 引数

  * `face_index`:[in] 交差点を計算する面のインデックス。
  * `ref_coords`:[in] 参照点の座標を含む配列。
  * `face_intersection`:[out] 参照空間内の面上の交差点を含む三次元配列。

### プロトタイプ

```c
void t8_geom_get_tet_face_intersection (const int face_index, const double *ref_coords, double face_intersection[3]);
```
