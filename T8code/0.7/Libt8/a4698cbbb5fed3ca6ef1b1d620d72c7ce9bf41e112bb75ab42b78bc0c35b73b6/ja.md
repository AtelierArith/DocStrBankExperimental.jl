```
t8_forest_get_local_or_ghost_id(forest, gtreeid)
```

グローバルツリーIDからこのツリーのフォレストローカルIDを計算します。ツリーがローカルツリーである場合、ローカルIDは0からローカルツリーの数の間になります。ツリーがゴーストである場合、ローカルIDはnum*local*treesからnum*local*trees + num*ghost*treesの間になります。ツリーがローカルツリーでもゴーストツリーでもない場合、負の数が返されます。

# 引数

  * `forest`:[in] フォレスト。
  * `gtreeid`:[in] ツリーのグローバルID。

# 戻り値

ツリーが*forest*内のローカルツリーである場合、そのローカルID。ゴーストツリーである場合はnum*local*trees + ゴーストID。そうでない場合は負の数。

# 参照

https://github.com/DLR-AMR/t8code/wiki/Tree-indexing ツリーインデクシングの詳細については。

### プロトタイプ

```c
t8_locidx_t t8_forest_get_local_or_ghost_id (const t8_forest_t forest, const t8_gloidx_t gtreeid);
```
