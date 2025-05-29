```
t8_cmesh_get_tree_class(cmesh, ltree_id)
```

与えられたローカルツリーのeclassを返します。TODO: インデックスを参照するべきか、それともctree_tを使用すべきか？

# 引数

  * `cmesh`:[in] 考慮すべきcmesh。
  * `tree_id`:[in] eclassが返されるツリーのローカルID。

# 戻り値

与えられたツリーのeclass。TODO: tree*idの代わりにltree*idやgtree_idなどのツリーIDを呼び出すべきです。*cmesh*はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
t8_eclass_t t8_cmesh_get_tree_class (t8_cmesh_t cmesh, t8_locidx_t ltree_id);
```
