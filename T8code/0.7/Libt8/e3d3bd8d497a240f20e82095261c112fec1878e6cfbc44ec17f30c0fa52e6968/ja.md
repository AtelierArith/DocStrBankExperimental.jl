```
t8_geom_get_scaling_factor_face_through_volume_prism(face, ref_coords)
```

プリズム要素の体積を通じての面の変位のスケーリングファクターを計算します。

# 引数

  * `face_index`:[in] 変位した面のインデックス。
  * `ref_coords`:[in] 参照点の座標を含む配列。

# 戻り値

プリズム体積内の参照座標の点での面の変位のスケーリングファクター。

### プロトタイプ

```c
double t8_geom_get_scaling_factor_face_through_volume_prism (const int face, const double *ref_coords);
```
