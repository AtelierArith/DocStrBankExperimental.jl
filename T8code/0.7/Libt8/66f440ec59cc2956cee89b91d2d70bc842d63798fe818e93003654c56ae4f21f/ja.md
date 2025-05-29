```
t8_cmesh_get_face_neighbor(cmesh, ltreeid, face, dual_face, orientation)
```

与えられたローカルツリーIDとフェイス番号に基づいて、フェイス隣接ツリーに関する情報を取得します。

!!! note
    *ltreeid* がゴーストであり、隣接するものがローカルツリーでもゴーストでもない場合、返り値は負になります。したがって、負の返り値は必ずしもドメイン境界を意味するわけではありません。ツリーがドメイン境界であるかどうかを確認するには


# 引数

  * `cmesh`:[in] 考慮すべきcmesh。
  * `ltreeid`:[in] ツリーまたはゴーストのローカルID。
  * `face`:[in] ツリー/ゴーストのフェイス番号。
  * `dual_face`:[out] NULLでない場合、この接続における隣接ツリーのフェイス番号。
  * `orientation`:[out] NULLでない場合、接続のフェイスの向き。

# 戻り値

非負の場合: 隣接ツリーまたはゴーストのローカルID。負の場合: このフェイスを越える隣接者は存在しません。*dual_face* と *orientation* は変更されません。

# 参照

[`t8_cmesh_tree_face_is_boundary`](@ref)。

### プロトタイプ

```c
t8_locidx_t t8_cmesh_get_face_neighbor (const t8_cmesh_t cmesh, const t8_locidx_t ltreeid, const int face, int *dual_face, int *orientation);
```
