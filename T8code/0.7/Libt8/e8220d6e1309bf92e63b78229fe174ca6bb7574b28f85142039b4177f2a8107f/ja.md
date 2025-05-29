```
t8_cmesh_trees_get_face_info(trees, ltreeid, face, ttf)
```

指定された面での木の隣接面を返し、tree*to*face情報を返します。

# 引数

  * `trees`:[in] 木を検索するための木構造。
  * `ltreeid`:[in] 木のローカルID。
  * `face`:[in] 木の面。
  * `ttf`:[out] NULLでない場合、面接続のtree*to*face値。

# 戻り値

この面に保存されている隣接面

### プロトタイプ

```c
t8_locidx_t t8_cmesh_trees_get_face_info (t8_cmesh_trees_t trees, t8_locidx_t ltreeid, int face, int8_t *ttf);
```
