```
p4est_mesh_face_neighbor_data(mfn, ghost_data)
```

現在の面の隣接者のユーザーデータを取得します。

### パラメータ

  * `mfn`:[in] イテレータの内部状態。
  * `ghost_data`:[in] [`p4est_ghost_exchange_data`](@ref) と同期されたゴースト四分木のデータ。

### 戻り値

現在の隣接者のユーザーデータへのポインタ。

### プロトタイプ

```c
void *p4est_mesh_face_neighbor_data (p4est_mesh_face_neighbor_t * mfn, void *ghost_data);
```
