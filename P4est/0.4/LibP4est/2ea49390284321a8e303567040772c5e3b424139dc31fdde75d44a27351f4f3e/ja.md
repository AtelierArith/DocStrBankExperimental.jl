```
p8est_mesh_face_neighbor_init2(mfn, p8est_, ghost, mesh, which_tree, quadrant_id)
```

クアドラントインデックスによってメッシュ隣接イテレータを初期化します。

### パラメータ

  * `mfn`:[out] 初期化される [`p8est_mesh_face_neighbor_t`](@ref)。
  * `which_tree`:[in] 隣接するクアドラントをループする木。
  * `quadrant_id`:[in] which_tree に対するクアドラントのインデックス。

### プロトタイプ

```c
void p8est_mesh_face_neighbor_init2 (p8est_mesh_face_neighbor_t * mfn, p8est_t * p8est, p8est_ghost_t * ghost, p8est_mesh_t * mesh, p4est_topidx_t which_tree, p4est_locidx_t quadrant_id);
```
