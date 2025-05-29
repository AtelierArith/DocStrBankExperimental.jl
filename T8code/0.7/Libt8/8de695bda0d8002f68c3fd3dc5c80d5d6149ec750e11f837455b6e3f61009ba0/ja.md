```
t8_cmesh_get_tree(cmesh, ltree_id)
```

指定されたローカルツリーへのポインタを返します。

# 引数

  * `cmesh`:[in] クエリされるcmesh。
  * `ltree_id`:[in] 要求されるツリーのローカルID。

# 戻り値

ローカルID *ltree_id* を持つ *cmesh* 内のツリーへのポインタ。 この関数を呼び出すとき、*cmesh* は少なくとも *ltree_id* + 1 のローカルツリーを持っている必要があります。 *cmesh* はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
t8_ctree_t t8_cmesh_get_tree (t8_cmesh_t cmesh, t8_locidx_t ltree_id);
```
