```
t8_forest_get_coarse_tree(forest, ltreeid)
```

森林内の木のローカルIDを指定すると、この木に対応するcmeshの粗い木を返します。

# 引数

  * `forest`:[in] 森。
  * `ltreeid`:[in] 森の木のローカルID。

# 戻り値

ローカルID *ltreeid* を持つ森林の木に一致する粗い木。

### プロトタイプ

```c
t8_ctree_t t8_forest_get_coarse_tree (t8_forest_t forest, t8_locidx_t ltreeid);
```
