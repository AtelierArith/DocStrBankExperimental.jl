```
t8_cmesh_trees_get_ghost(trees, lghost)
```

特定のゴーストへのポインタをtrees構造体から返します。

# 引数

  * `trees`:[in] ツリーを検索するためのツリー構造。
  * `lghost`:[in] ゴーストのローカルID。

# 戻り値

ローカルID *ghost* を持つゴーストへのポインタ。

### プロトタイプ

```c
t8_cghost_t t8_cmesh_trees_get_ghost (t8_cmesh_trees_t trees, t8_locidx_t lghost);
```
