```
p8est_connectivity_face_neighbor_edge(e, f, nf, o)
```

隣接する面の1つを横切るエッジを隣接木に変換します。このバージョンは、隣接面と向きを別々に期待します。

`.`

### パラメータ

  * `e`:[in] 0..11の範囲のエッジ番号。
  * `f`:[in] エッジ *e* に接触する面 0..5。
  * `nf`:[in] の反対側にある隣接面。
  * `o`:[in] 木の境界面 *f* との間の向き。

### 戻り値

隣接面から見たエッジの番号。

### プロトタイプ

```c
int p8est_connectivity_face_neighbor_edge (int e, int f, int nf, int o);
```
