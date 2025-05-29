```
p4est_connectivity_new(num_vertices, num_trees, num_corners, num_ctt)
```

接続構造体を割り当てます。属性フィールドはNULLに初期化されます。

### パラメータ

  * `num_vertices`:[in] 総頂点数（すなわち、幾何学的ポイント）。
  * `num_trees`:[in] 森の中の木の数。
  * `num_corners`:[in] 木を接続するコーナーの数。
  * `num_ctt`:[in] corner*to*tree配列の総木の数。

### 戻り値

割り当てられた配列を持つ接続構造体。

### プロトタイプ

```c
p4est_connectivity_t *p4est_connectivity_new (p4est_topidx_t num_vertices, p4est_topidx_t num_trees, p4est_topidx_t num_corners, p4est_topidx_t num_ctt);
```
