```
t8_cmesh_trees_get_tree_ext(trees, ltree_id, face_neigh, ttf)
```

特定の木を trees 構造体から取得し、その face*neighbor および tree*to_face 配列へのポインタを返します。

# 引数

  * `trees`:[in] 木を検索するための trees 構造体。
  * `ltree_id`:[in] 木のローカル ID。
  * `face_neigh`:[out] NULL でない場合、返り値として trees の face_neighbor 配列へのポインタがここに格納されます。
  * `ttf`:[out] NULL でない場合、返り値として trees の tree*to*face 配列へのポインタがここに格納されます。

# 戻り値

ローカル ID *tree* を持つ木へのポインタ。

### プロトタイプ

```c
t8_ctree_t t8_cmesh_trees_get_tree_ext (t8_cmesh_trees_t trees, t8_locidx_t ltree_id, t8_locidx_t **face_neigh, int8_t **ttf);
```
