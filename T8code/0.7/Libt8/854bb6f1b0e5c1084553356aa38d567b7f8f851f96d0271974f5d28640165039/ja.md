```
t8_forest_ghost_get_ghost_treeid(forest, gtreeid)
```

グローバルツリーからそのゴーストローカルツリーIDを計算します。

# 引数

  * `forest`:[in] フォレスト。ゴーストレイヤーが存在する必要があります。
  * `gtreeid`:[in] *forest*内のグローバルツリー。

# 戻り値

*gtreeid*がゴーストツリーでもある場合、そのツリーのghost->ghost_trees配列内のインデックスを返します。そうでない場合は負の数を返します。*forest*はこの関数を呼び出す前にコミットされている必要があります。

# 参照

https://github.com/DLR-AMR/t8code/wiki/Tree-indexing でツリーインデクシングの詳細を確認してください。

### プロトタイプ

```c
t8_locidx_t t8_forest_ghost_get_ghost_treeid (t8_forest_t forest, t8_gloidx_t gtreeid);
```
