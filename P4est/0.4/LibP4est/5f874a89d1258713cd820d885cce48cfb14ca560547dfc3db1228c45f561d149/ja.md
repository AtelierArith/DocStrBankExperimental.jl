```
p8est_ghost_tree_contains(ghost, which_proc, which_tree, q)
```

ゴーストレイヤーの範囲で先祖を二分探索します。

### パラメータ

  * `ghost`:[in] ゴーストレイヤー。
  * `which_proc`:[in] 検索される象限の所有者。-1 である可能性があります。
  * `which_tree`:[in] 検索される象限の木。-1 である可能性があります。
  * `q`:[in] 有効な象限の先祖が検索されます。

### 戻り値

ゴーストレイヤー内のオフセット、または見つからなかった場合は -1。

### プロトタイプ

```c
ssize_t p8est_ghost_tree_contains (p8est_ghost_t * ghost, int which_proc, p4est_topidx_t which_tree, const p8est_quadrant_t * q);
```
