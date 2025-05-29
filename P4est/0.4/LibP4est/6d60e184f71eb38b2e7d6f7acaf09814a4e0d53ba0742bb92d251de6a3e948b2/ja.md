```
p4est_mesh_face_neighbor_next(mfn, ntree, nquad, nface, nrank)
```

イテレータを前に進めて、四分木の隣接点をループします。

### パラメータ

  * `mfn`:[in,out] イテレータの内部状態。
  * `ntree`:[out] NULLでない場合、隣接点の木の番号。
  * `nquad`:[out] NULLでない場合、木の中の四分木の番号。ゴーストの場合は、ゴースト層内の番号。
  * `nface`:[out] NULLでない場合、[`p4est_mesh_t`](@ref)における隣接点の面。
  * `nrank`:[out] NULLでない場合、隣接点の所有プロセス。

### 戻り値

実際の四分木またはゴースト層からのものを返します。イテレータが完了した場合はNULLを返します。

### プロトタイプ

```c
p4est_quadrant_t *p4est_mesh_face_neighbor_next (p4est_mesh_face_neighbor_t * mfn, p4est_topidx_t * ntree, p4est_locidx_t * nquad, int *nface, int *nrank);
```
