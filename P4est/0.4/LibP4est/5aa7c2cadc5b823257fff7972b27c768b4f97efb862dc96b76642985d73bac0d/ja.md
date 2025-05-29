```
p8est_mesh_face_neighbor_next(mfn, ntree, nquad, nface, nrank)
```

イテレータを前に進めて、四分木の隣接点をループします。

### パラメータ

  * `mfn`:[in,out] イテレータの内部状態。
  * `ntree`:[out] NULLでない場合、隣接点の木の番号。
  * `nquad`:[out] NULLでない場合、木の中の四分木の番号。ゴーストの場合はゴースト層内の番号。
  * `nface`:[out] NULLでない場合、隣接点の面 [`p8est_mesh_t`](@ref) のように。
  * `nrank`:[out] NULLでない場合、隣接点の所有プロセス。

### 戻り値

実際の四分木またはゴースト層のものを返します。イテレータが完了した場合はNULLを返します。

### プロトタイプ

```c
p8est_quadrant_t *p8est_mesh_face_neighbor_next (p8est_mesh_face_neighbor_t * mfn, p4est_topidx_t * ntree, p4est_locidx_t * nquad, int *nface, int *nrank);
```
