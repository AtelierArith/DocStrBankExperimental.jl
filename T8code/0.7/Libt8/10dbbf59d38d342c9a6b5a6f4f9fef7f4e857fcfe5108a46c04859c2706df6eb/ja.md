```
t8_cmesh_trees_add_tree(trees, ltree_id, proc, eclass)
```

ツリー構造にツリーを追加します。

# 引数

  * `trees`:[in,out] 更新されるツリー構造。
  * `tree_id`:[in] 挿入されるツリーのローカルID。
  * `proc`:[in] ツリーが受信されたプロセスのmpirank。
  * `eclass`:[in] ツリーの要素クラス。

### プロトタイプ

```c
void t8_cmesh_trees_add_tree (t8_cmesh_trees_t trees, t8_locidx_t ltree_id, int proc, t8_eclass_t eclass);
```
