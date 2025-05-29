```
t8_cmesh_trees_get_ghost_local_id(trees, global_id)
```

与えられたグローバルツリーIDのゴーストツリーがツリー構造内にある場合、そのローカルゴーストIDを返します。

# 引数

  * `trees`:[in] ツリー構造。
  * `global_id`:[in] グローバルツリーID。

# 戻り値

ツリー *global_id* のローカルIDが *trees* 内にゴーストである場合はそのIDを返します。そうでない場合は負の数を返します。ローカルIDは、num*local*trees <= *l* < num*local*trees + num_ghosts である数 l です。

### プロトタイプ

```c
t8_locidx_t t8_cmesh_trees_get_ghost_local_id (t8_cmesh_trees_t trees, t8_gloidx_t global_id);
```
