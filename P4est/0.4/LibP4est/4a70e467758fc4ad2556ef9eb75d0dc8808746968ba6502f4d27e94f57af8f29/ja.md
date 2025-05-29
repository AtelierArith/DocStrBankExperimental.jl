```
p4est_mesh_face_neighbor_init2(mfn, p4est_, ghost, mesh, which_tree, quadrant_id)
```

クアドラントインデックスによってメッシュ隣接イテレータを初期化します。

### パラメータ

  * `mfn`:[out] 初期化される [`p4est_mesh_face_neighbor_t`](@ref)。
  * `which_tree`:[in] 隣接するクアドラントをループするツリー。
  * `quadrant_id`:[in] which_tree に対するクアドラントのインデックス。

### プロトタイプ

```c
void p4est_mesh_face_neighbor_init2 (p4est_mesh_face_neighbor_t * mfn, p4est_t * p4est, p4est_ghost_t * ghost, p4est_mesh_t * mesh, p4est_topidx_t which_tree, p4est_locidx_t quadrant_id);
```
