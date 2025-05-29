```
p8est_partition_lnodes(p8est_, ghost, degree, partition_for_coarsening)
```

ノード数に基づいて重みを使用してパーティションを作成します。

### パラメータ

  * `p8est`:[in,out] 再パーティション化されるフォレスト
  * `ghost`:[in] ゴーストレイヤー
  * `degree`:[in] [`p8est_lnodes_new`](@ref)() に渡される度数
  * `partition_for_coarsening`:[in] パーティションが粗化を許可するかどうか（すなわち、マージされる可能性のある兄弟をグループ化するか）

### プロトタイプ

```c
void p8est_partition_lnodes (p8est_t * p8est, p8est_ghost_t * ghost, int degree, int partition_for_coarsening);
```
