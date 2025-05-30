```
t8_cmesh_trees_get_face_neighbor_ext(tree, face, ttf)
```

粗い木と面番号を与えると、隣接する木のローカルIDとその木から面への情報を返します。

# 引数

  * `tree`:[in] 粗い木。
  * `face`:[in] 面番号。
  * `ttf`:[out] NULLでない場合、この面の木から面への値で埋められます。

# 戻り値

隣接する木のローカルID。

### プロトタイプ

```c
t8_locidx_t t8_cmesh_trees_get_face_neighbor_ext (const t8_ctree_t tree, const int face, int8_t *ttf);
```
