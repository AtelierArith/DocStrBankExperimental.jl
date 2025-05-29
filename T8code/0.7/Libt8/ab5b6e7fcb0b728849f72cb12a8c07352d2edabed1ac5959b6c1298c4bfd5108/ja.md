```
t8_cmesh_trees_add_ghost(trees, lghost_index, gtree_id, proc, eclass, num_local_trees)
```

ツリー構造にゴーストを追加します。

# 引数

  * `trees`:[in,out] 更新されるツリー構造。
  * `ghost_index`:[in] 挿入されるゴーストの部分配列内のインデックス。
  * `tree_id`:[in] ゴーストのグローバルインデックス。
  * `proc`:[in] ゴーストが受信されたプロセスのmpirank。
  * `eclass`:[in] ゴーストの要素クラス。
  * `num_local_trees`:[in] cmesh内のローカルツリーの数。

### プロトタイプ

```c
void t8_cmesh_trees_add_ghost (t8_cmesh_trees_t trees, t8_locidx_t lghost_index, t8_gloidx_t gtree_id, int proc, t8_eclass_t eclass, t8_locidx_t num_local_trees);
```
