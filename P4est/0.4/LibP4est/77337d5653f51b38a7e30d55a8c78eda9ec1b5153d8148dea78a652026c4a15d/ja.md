```
p8est_connectivity_edge_neighbor_edge_corner(ec, o)
```

隣接するエッジの1つを介してエッジコーナーを隣接木に変換します。

### パラメータ

  * `ec`:[in] 0..1の範囲のエッジコーナー番号。
  * `o`:[in] 木の境界エッジ接続の向き。

### 戻り値

他の木から見たエッジコーナー番号。

### プロトタイプ

```c
int p8est_connectivity_edge_neighbor_edge_corner (int ec, int o);
```
