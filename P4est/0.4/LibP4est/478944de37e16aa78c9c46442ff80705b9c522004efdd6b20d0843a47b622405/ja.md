```
p8est_connectivity_face_neighbor_face_edge(fe, f, nf, o)
```

隣接する面の1つを介して面-エッジを隣接木に変換します。このバージョンは、隣接面と向きを別々に期待します。

`.`

### パラメータ

  * `fe`:[in] 0..3の範囲の面エッジ番号。
  * `f`:[in] エッジ *e* に接触する面番号。
  * `nf`:[in] の反対側にある隣接面。
  * `o`:[in] 木の境界面 *f* との間の向き。

### 戻り値

隣接木から見た面エッジ番号。

### プロトタイプ

```c
int p8est_connectivity_face_neighbor_face_edge (int fe, int f, int nf, int o);
```
