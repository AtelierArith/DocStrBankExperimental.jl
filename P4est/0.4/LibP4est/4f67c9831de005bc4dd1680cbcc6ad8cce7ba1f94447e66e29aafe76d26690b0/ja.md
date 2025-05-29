```
p8est_mesh_face_neighbor_init(mfn, p8est_, ghost, mesh, which_tree, quadrant)
```

クアドラントポインタによってメッシュ隣接イテレータを初期化します。

### パラメータ

  * `mfn`:[out] 初期化される [`p8est_mesh_face_neighbor_t`](@ref)。
  * `which_tree`:[in] 隣接するクアドラントをループするツリー。
  * `quadrant`:[in] which_tree に含まれるクアドラントへのポインタ。

### プロトタイプ

```c
void p8est_mesh_face_neighbor_init (p8est_mesh_face_neighbor_t * mfn, p8est_t * p8est, p8est_ghost_t * ghost, p8est_mesh_t * mesh, p4est_topidx_t which_tree, p8est_quadrant_t * quadrant);
```
