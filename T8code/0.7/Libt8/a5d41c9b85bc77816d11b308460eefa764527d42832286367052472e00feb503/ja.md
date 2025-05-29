```
t8_cmesh_trees_get_face_neighbor_ext(tree, face, ttf)
```

粗いツリーと面番号が与えられた場合、隣接ツリーのローカルIDとそのツリーから面への情報を返します。

# 引数

  * `tree`:[in] 粗いツリー。
  * `face`:[in] 面番号。
  * `ttf`:[out] NULLでない場合、この面のツリーから面への値で埋められます。

# 戻り値

隣接ツリーのローカルID。

### プロトタイプ

```c
t8_locidx_t t8_cmesh_trees_get_face_neighbor_ext (const t8_ctree_t tree, const int face, int8_t *ttf);
```
