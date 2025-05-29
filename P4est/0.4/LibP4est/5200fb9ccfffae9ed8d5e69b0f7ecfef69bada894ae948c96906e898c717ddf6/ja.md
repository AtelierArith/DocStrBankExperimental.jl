```
p4est_mesh_new_ext(p4est_, ghost, compute_tree_index, compute_level_lists, btype)
```

新しいメッシュを作成します。

### パラメータ

  * `p4est`:[in] 完全に2:1バランスの取れたフォレスト。
  * `ghost`:[in] 提供された`p4est`から作成されたゴーストレイヤー。
  * `compute_tree_index`:[in] quad*to*treeリストを割り当てて計算するかどうかを決定するブール値。
  * `compute_level_lists`:[in] quad_level内のレベルリストを計算するかどうかを決定するブール値。
  * `btype`:[in] 現在無視されており、面の隣接のみが保存されます。

### 戻り値

完全に割り当てられたメッシュ構造。

### プロトタイプ

```c
p4est_mesh_t *p4est_mesh_new_ext (p4est_t * p4est, p4est_ghost_t * ghost, int compute_tree_index, int compute_level_lists, p4est_connect_type_t btype);
```
