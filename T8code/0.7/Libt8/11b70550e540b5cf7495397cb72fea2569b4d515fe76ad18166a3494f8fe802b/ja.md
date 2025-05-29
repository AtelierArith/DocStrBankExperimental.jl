```
t8_forest_get_tree(forest, ltree_id)
```

森林内の木へのポインタを返します。

# 引数

  * `forest`:[in] 森。
  * `ltree_id`:[in] 木のローカルID。

# 戻り値

ローカルID *ltree_id* を持つ木へのポインタ。*forest* はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
t8_tree_t t8_forest_get_tree (const t8_forest_t forest, const t8_locidx_t ltree_id);
```
