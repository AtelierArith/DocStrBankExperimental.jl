```
t8_forest_tree_get_leaves(forest, ltree_id)
```

フォレスト内のローカルツリーの葉要素の配列を返します。

# 引数

  * `forest`:[in] フォレスト。
  * `ltree_id`:[in] *forest* のローカルツリーのローカルID。

# 戻り値

このツリーのすべての葉要素を格納する [`t8_element_t`](@ref) の配列。

### プロトタイプ

```c
t8_element_array_t * t8_forest_tree_get_leaves (const t8_forest_t forest, const t8_locidx_t ltree_id);
```
