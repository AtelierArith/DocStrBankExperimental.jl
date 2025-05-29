```
t8_cmesh_trees_get_face_neighbor(tree, face)
```

粗い木と面番号が与えられた場合、隣接する木のローカルIDを返します。

# 引数

  * `tree.`:[in] 粗い木。
  * `face.`:[in] 面番号。

# 戻り値

隣接する木のローカルID。

### プロトタイプ

```c
t8_locidx_t t8_cmesh_trees_get_face_neighbor (const t8_ctree_t tree, const int face);
```
