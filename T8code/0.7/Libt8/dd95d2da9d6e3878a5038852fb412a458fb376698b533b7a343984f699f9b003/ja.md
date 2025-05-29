```
t8_forest_get_tree_class(forest, ltreeid)
```

森林内の木のクラスを返します。

# 引数

  * `forest`:[in] 森。
  * `ltreeid`:[in] *forest*内の木のローカルID（ローカルまたはゴースト）。

# 戻り値

ローカルID *ltreeid*を持つ木の要素クラス。

### プロトタイプ

```c
t8_eclass_t t8_forest_get_tree_class (const t8_forest_t forest, const t8_locidx_t ltreeid);
```
