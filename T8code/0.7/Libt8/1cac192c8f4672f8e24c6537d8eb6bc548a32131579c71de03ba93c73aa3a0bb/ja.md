```
t8_cmesh_get_global_id(cmesh, local_id)
```

与えられたローカルツリーまたはゴーストのグローバルIDを返します。

# 引数

  * `cmesh`:[in] 考慮すべきcmesh。
  * `local_id`:[in] ツリーまたはゴーストのローカルID。*local_id* < cmesh.num*local*trees の場合はツリー、それ以外はゴーストです。

# 戻り値

ツリー/ゴーストのグローバルID。

# 参照

https://github.com/DLR-AMR/t8code/wiki/Tree-indexing ツリーインデックスに関する詳細については。

### プロトタイプ

```c
t8_gloidx_t t8_cmesh_get_global_id (t8_cmesh_t cmesh, t8_locidx_t local_id);
```
