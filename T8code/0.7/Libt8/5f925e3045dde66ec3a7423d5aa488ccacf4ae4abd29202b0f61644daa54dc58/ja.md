```
t8_forest_global_tree_id(forest, ltreeid)
```

ローカルツリーまたはゴーストツリーのグローバルIDを返します。

# 引数

  * `forest`:[in] 森。
  * `ltreeid`:[in] ローカルツリーまたはゴーストツリーを指定するID 0 <= *ltreeid* < num*local*trees + num_ghosts。

# 戻り値

ローカルID *ltreeid* に対応するツリーのグローバルID。*forest* はこの関数を呼び出す前にコミットされている必要があります。

# 参照

https://github.com/DLR-AMR/t8code/wiki/Tree-indexing でツリーインデックスに関する詳細を確認してください。

### プロトタイプ

```c
t8_gloidx_t t8_forest_global_tree_id (const t8_forest_t forest, const t8_locidx_t ltreeid);
```
