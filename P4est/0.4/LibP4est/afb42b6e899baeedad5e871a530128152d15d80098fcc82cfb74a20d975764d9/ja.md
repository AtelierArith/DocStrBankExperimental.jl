```
p8est_connectivity_face_neighbor_corner(c, f, nf, o)
```

隣接する面の1つを通じてコーナーを隣接木に変換します。このバージョンは、隣接面と向きを別々に期待します。

`.`

### パラメータ

  * `c`:[in] 0..7の範囲のコーナー番号。
  * `f`:[in] コーナー *c* に接触する面番号。
  * `nf`:[in] の反対側にある隣接面。
  * `o`:[in] 木の境界面 *f* と の間の向き。

### 戻り値

隣接木から見たコーナーの番号。

### プロトタイプ

```c
int p8est_connectivity_face_neighbor_corner (int c, int f, int nf, int o);
```
