```
p8est_connectivity_face_neighbor_face_corner(fc, f, nf, o)
```

隣接する面の1つを通じて面のコーナーを隣接木に変換します。このバージョンは、隣接面と向きを別々に期待します。

`.`

### パラメータ

  * `fc`:[in] 0..3の範囲の面コーナー番号。
  * `f`:[in] 面コーナー *fc* が相対する面。
  * `nf`:[in] の反対側にある隣接面。
  * `o`:[in] 木の境界面 *f* との間の向き。

### 戻り値

隣接面に対する面コーナー番号。

### プロトタイプ

```c
int p8est_connectivity_face_neighbor_face_corner (int fc, int f, int nf, int o);
```
