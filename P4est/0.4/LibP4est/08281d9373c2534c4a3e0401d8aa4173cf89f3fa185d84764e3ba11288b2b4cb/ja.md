```
p8est_connectivity_edge_neighbor_corner(c, e, ne, o)
```

隣接するエッジの1つを介してコーナーを隣接ツリーに変換します。このバージョンは、隣接エッジと向きを別々に期待します。

### パラメータ

  * `c`:[in] 0..7のコーナー番号。
  * `e`:[in] コーナー *c* に接触するエッジ 0..11。
  * `ne`:[in] *.* の反対側にある隣接エッジ。
  * `o`:[in] ツリー境界エッジ *e* と *.* の間の向き。

### 戻り値

隣接から見たコーナー番号。

### プロトタイプ

```c
int p8est_connectivity_edge_neighbor_corner (int c, int e, int ne, int o);
```
