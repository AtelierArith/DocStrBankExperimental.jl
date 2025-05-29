```
t8_offset_all_owners_of_tree(mpisize, gtree, offset, owners)
```

特定の木を所有するすべてのプロセスのリストを計算します。*offset* マイナス 1。

# 引数

  * `mpisize`:[in] MPI ランクの数、また *offset* マイナス 1 のエントリの数。
  * `gtree`:[in] 木のグローバルインデックス。
  * `offset`:[in] 考慮すべきパーティション。
  * `owners`:[in,out] 入力時に整数エントリとゼロ要素を持つ初期化された [`sc_array`](@ref)。出力時に *gtree* を *offset* のローカルツリーとして持つすべての MPI ランクのソートされたリスト。

### プロトタイプ

```c
void t8_offset_all_owners_of_tree (const int mpisize, const t8_gloidx_t gtree, const t8_gloidx_t *offset, sc_array_t *owners);
```
