```
t8_cmesh_get_ghost_class(cmesh, lghost_id)
```

与えられたローカルゴーストのeclassを返します。TODO: インデックスを参照すべきか、それともcghost_tを使用すべきか？

# 引数

  * `cmesh`:[in] 考慮すべきcmesh。
  * `ghost_id`:[in] eclassが返されるゴーストのローカルID。0 <= *tree_id* < cmesh.num_ghosts。

# 戻り値

与えられたゴーストのeclass。*cmesh*はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
t8_eclass_t t8_cmesh_get_ghost_class (t8_cmesh_t cmesh, t8_locidx_t lghost_id);
```
