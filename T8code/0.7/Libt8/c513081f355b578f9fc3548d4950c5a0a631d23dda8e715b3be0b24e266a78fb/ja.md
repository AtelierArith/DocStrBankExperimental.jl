```
t8_forest_get_tree_num_elements(forest, ltreeid)
```

木の要素の数を返します。

# 引数

  * `forest`:[in] 森。
  * `ltreeid`:[in] 木のローカルID。

# 戻り値

ローカルツリー *ltreeid* の要素の数。

### プロトタイプ

```c
t8_locidx_t t8_forest_get_tree_num_elements (t8_forest_t forest, t8_locidx_t ltreeid);
```
