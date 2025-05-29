```
p6est_tree_get_vertices(conn, which_tree, vertices)
```

ツリーのコーナーの頂点を取得します。

### パラメータ

  * `conn`:[in] 2D+1D 接続構造
  * `which_tree`:[in] 森の中のツリー
  * `vertices`:[out] ツリーのコーナーの座標

### プロトタイプ

```c
void p6est_tree_get_vertices (p6est_connectivity_t * conn, p4est_topidx_t which_tree, double vertices[24]);
```
