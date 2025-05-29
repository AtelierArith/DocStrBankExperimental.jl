```
t8_forest_tree_is_local(forest, local_tree)
```

与えられたツリーIDが森林内のローカルツリーに属するかどうかを確認します。

# 引数

  * `forest`:[in] 森林。
  * `local_tree`:[in] ツリーID。

# 戻り値

ID *local_tree* が *forest* のローカルツリーに属する場合にのみ真を返します。*forest* はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
int t8_forest_tree_is_local (const t8_forest_t forest, const t8_locidx_t local_tree);
```
