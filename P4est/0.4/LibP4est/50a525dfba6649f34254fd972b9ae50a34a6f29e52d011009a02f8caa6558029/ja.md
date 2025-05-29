```
p4est_ghost_bsearch(ghost, which_proc, which_tree, q)
```

ゴーストレイヤーの範囲での正確な一致のための二分探索を実施します。

### パラメータ

  * `ghost`:[in] ゴーストレイヤー。
  * `which_proc`:[in] 検索された四分木の所有者。-1 である可能性があります。
  * `which_tree`:[in] 検索された四分木の木。-1 である可能性があります。
  * `q`:[in] ゴーストレイヤー内で検索される有効な四分木。

### 戻り値

ゴーストレイヤー内のオフセット、または見つからなかった場合は -1。

### プロトタイプ

```c
ssize_t p4est_ghost_bsearch (p4est_ghost_t * ghost, int which_proc, p4est_topidx_t which_tree, const p4est_quadrant_t * q);
```
