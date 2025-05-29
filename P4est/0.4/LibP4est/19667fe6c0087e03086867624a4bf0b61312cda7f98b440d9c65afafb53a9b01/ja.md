```
p8est_partition_lnodes_detailed(p4est_, ghost, nodes_per_volume, nodes_per_face, nodes_per_edge, nodes_per_corner, partition_for_coarsening)
```

ボリューム、フェイス、エッジ、またはコーナーにどこに存在するかによって分解された重みを使用してパーティションを作成します。

### プロトタイプ

```c
void p8est_partition_lnodes_detailed (p8est_t * p4est, p8est_ghost_t * ghost, int nodes_per_volume, int nodes_per_face, int nodes_per_edge, int nodes_per_corner, int partition_for_coarsening);
```
