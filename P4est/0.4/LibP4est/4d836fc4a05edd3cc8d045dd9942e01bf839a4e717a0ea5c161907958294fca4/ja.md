```
p4est_iterate_ext(p4est_, ghost_layer, user_data, iter_volume, iter_face, iter_corner, remote)
```

[`p4est_iterate_ext`](@ref) はオプション *remote* を追加します: これが false の場合、[`p4est_iterate`](@ref) と同じです; これが true の場合、ローカル四分木に触れたハンギングフェイスのコーナーでもコーナーコールバックが呼び出されます。

### プロトタイプ

```c
void p4est_iterate_ext (p4est_t * p4est, p4est_ghost_t * ghost_layer, void *user_data, p4est_iter_volume_t iter_volume, p4est_iter_face_t iter_face, p4est_iter_corner_t iter_corner, int remote);
```
