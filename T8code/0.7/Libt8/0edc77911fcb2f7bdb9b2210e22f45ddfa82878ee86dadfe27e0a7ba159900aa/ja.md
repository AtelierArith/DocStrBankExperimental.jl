```
t8_cmesh_trees_get_tree(trees, ltree)
```

特定の木をtrees構造体から取得するためのポインタを返します。

# 引数

  * `trees`:[in] 木を検索するためのtress構造体。
  * `ltree`:[in] 木のローカルID。

# 戻り値

ローカルID *tree* を持つ木へのポインタ。

### プロトタイプ

```c
t8_ctree_t t8_cmesh_trees_get_tree (t8_cmesh_trees_t trees, t8_locidx_t ltree);
```
