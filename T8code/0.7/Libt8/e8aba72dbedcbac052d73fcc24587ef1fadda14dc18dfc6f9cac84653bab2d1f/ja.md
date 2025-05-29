```
t8_cmesh_get_local_id(cmesh, global_id)
```

与えられたグローバルツリーのローカルIDを返します。

# 引数

  * `cmesh`:[in] cmesh。
  * `global_id`:[in] グローバルツリーID。

# 戻り値

*global_id* がローカルツリーに対応する場合は、値 l 0 <= *l* < num*local*trees を返します。*global_id* がゴーストツリーに対応する場合は、num*local*trees <= *l* < num*local*trees + num*ghosts を返します。*global*id* がローカルツリーまたはゴーストツリーのいずれにも一致しない場合は、負の値を返します。

# 参照

https://github.com/DLR-AMR/t8code/wiki/Tree-indexing ツリーインデクシングの詳細については。

### プロトタイプ

```c
t8_locidx_t t8_cmesh_get_local_id (t8_cmesh_t cmesh, t8_gloidx_t global_id);
```
