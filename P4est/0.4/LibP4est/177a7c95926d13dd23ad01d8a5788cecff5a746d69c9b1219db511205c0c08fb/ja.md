```
p4est_partition_lnodes(p4est_, ghost, degree, partition_for_coarsening)
```

ノードに割り当てられた数に基づいて重みを使用してパーティションを作成します

### パラメータ

  * `p4est`:[in,out] 再パーティション化されるフォレスト
  * `ghost`:[in] ゴーストレイヤー
  * `degree`:[in] [`p4est_lnodes_new`](@ref)() に渡される度数
  * `partition_for_coarsening`:[in] パーティションが粗化を許可するべきかどうか（すなわち、マージされる可能性のある兄弟をグループ化する）

### プロトタイプ

```c
void p4est_partition_lnodes (p4est_t * p4est, p4est_ghost_t * ghost, int degree, int partition_for_coarsening);
```
