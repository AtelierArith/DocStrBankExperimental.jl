```
p8est_mesh_new_ext(p4est_, ghost, compute_tree_index, compute_level_lists, btype)
```

新しいメッシュを作成します。

### パラメータ

  * `p8est`:[in] 完全に2:1バランスの取れたフォレスト。
  * `ghost`:[in] 提供された `p4est` から作成されたゴーストレイヤー。
  * `compute_tree_index`:[in] quad*to*treeリストを割り当てて計算するかどうかを決定するブール値。
  * `compute_level_lists`:[in] quad_levelでレベルリストを計算するかどうかを決定するブール値。
  * `btype`:[in] 現在無視されており、隣接する面のみが保存されます。

### 戻り値

完全に割り当てられたメッシュ構造体。

### プロトタイプ

```c
p8est_mesh_t *p8est_mesh_new_ext (p8est_t * p4est, p8est_ghost_t * ghost, int compute_tree_index, int compute_level_lists, p8est_connect_type_t btype);
```
