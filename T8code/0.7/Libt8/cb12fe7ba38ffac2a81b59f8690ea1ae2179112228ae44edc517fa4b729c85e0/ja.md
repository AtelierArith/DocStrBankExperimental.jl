```
t8_cmesh_trees_start_part(trees, proc, lfirst_tree, num_trees, lfirst_ghost, num_ghosts, alloc)
```

指定された数の木とゴーストを持つ木構造体の特定の tree*part の first*tree 配列を割り当てます。この関数は、木とゴーストのメモリを割り当てますが、それらの面隣接エントリや属性のためのメモリは割り当てません。これらは、木とゴーストの eclasses が知られるようになったときに後で割り当てる必要があります t8*cmesh*trees*finish*part。

# 引数

  * `trees`:[in,out] 更新される木構造。
  * `proc`:[in] 更新される部分のインデックス。
  * `lfirst_tree`:[in] その部分の最初の木のローカル ID。
  * `num_trees`:[in] その部分の木の数。
  * `lfirst_ghost`:[in] その部分の最初のゴーストのローカル ID。
  * `num_ghosts`:[in] その部分のゴーストの数。
  * `alloc`:[in] true の場合、木とゴーストの数に対して first_tree 配列が割り当てられます。cmesh がコピーされるとき、これを望まないため、alloc = 0 を渡します。

### プロトタイプ

```c
void t8_cmesh_trees_start_part (t8_cmesh_trees_t trees, int proc, t8_locidx_t lfirst_tree, t8_locidx_t num_trees, t8_locidx_t lfirst_ghost, t8_locidx_t num_ghosts, int alloc);
```
