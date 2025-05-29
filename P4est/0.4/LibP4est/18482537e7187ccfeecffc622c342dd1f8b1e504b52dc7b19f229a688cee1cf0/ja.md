```
p8est_find_edge_transform(connectivity, itree, iedge, ei)
```

エッジの隣接情報を含む配列を埋めます。

### パラメータ

  * `itree`:[in] 発信元ツリーの番号。
  * `iedge`:[in] 発信元エッジの番号。
  * `ei`:[in,out] 初期化された配列を持つ `p8est_edge_info_t` 構造体。

### プロトタイプ

```c
void p8est_find_edge_transform (p8est_connectivity_t * connectivity, p4est_topidx_t itree, int iedge, p8est_edge_info_t * ei);
```
