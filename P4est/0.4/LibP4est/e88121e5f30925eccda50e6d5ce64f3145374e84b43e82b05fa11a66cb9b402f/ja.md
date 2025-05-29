```
p8est_iterate_ext(p8est_, ghost_layer, user_data, iter_volume, iter_face, iter_edge, iter_corner, remote)
```

[`p8est_iterate_ext`](@ref) はオプション *remote* を追加します: これが false の場合、[`p8est_iterate`](@ref) と同じです; これが true の場合、ローカル四分木に触れたハンギング面/エッジのコーナー/エッジに対してもコーナー/エッジコールバックが呼び出されます。

### プロトタイプ

```c
void p8est_iterate_ext (p8est_t * p8est, p8est_ghost_t * ghost_layer, void *user_data, p8est_iter_volume_t iter_volume, p8est_iter_face_t iter_face, p8est_iter_edge_t iter_edge, p8est_iter_corner_t iter_corner, int remote);
```
