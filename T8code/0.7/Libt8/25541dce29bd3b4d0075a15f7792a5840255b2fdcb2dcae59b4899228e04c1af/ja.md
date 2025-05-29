```
t8_offset_prev_owner_of_tree(mpisize, gtree, offset, current_owner)
```

プロセス current_owner がローカルツリーとして gtree を持っている場合、次に小さいランクでこのツリーをローカルツリーとして持つランクを見つけます。

# 引数

  * `mpisize`:[in] MPI ランクの数、また *offset* のエントリ数から 1 を引いた数。
  * `gtree`:[in] ツリーのグローバル ID。
  * `offset`:[in] 考慮すべきパーティション。
  * `current_owner`:[in] *gtree* をローカルツリーとして持つプロセス。

# 戻り値

*gtree* をローカルツリーとして持つ current_owner よりも小さい次のランクの MPI ランク。該当するランクが存在しない場合は -1。

### プロトタイプ

```c
int t8_offset_prev_owner_of_tree (const int mpisize, const t8_gloidx_t gtree, const t8_gloidx_t *offset, const int current_owner);
```
