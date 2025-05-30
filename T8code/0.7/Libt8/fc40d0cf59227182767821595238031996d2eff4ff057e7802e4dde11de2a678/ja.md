```
t8_cmesh_trees_get_ghost_ext(trees, lghost_id, face_neigh, ttf)
```

特定のゴーストへのポインタをtrees構造体から返し、さらにそのface*neighborおよびtree*to_face配列へのポインタも返します。

# 引数

  * `trees`:[in] ゴーストを検索するtrees構造体。
  * `lghost_id`:[in] ゴーストのローカルID。
  * `face_neigh`:[out] NULLでない場合、ゴーストのface_neighbor配列へのポインタがここに格納されます。
  * `ttf`:[out] NULLでない場合、ゴーストのtree*to*face配列へのポインタがここに格納されます。

# 戻り値

ローカルID *tree* を持つ木へのポインタ。

### プロトタイプ

```c
t8_cghost_t t8_cmesh_trees_get_ghost_ext (t8_cmesh_trees_t trees, t8_locidx_t lghost_id, t8_gloidx_t **face_neigh, int8_t **ttf);
```
