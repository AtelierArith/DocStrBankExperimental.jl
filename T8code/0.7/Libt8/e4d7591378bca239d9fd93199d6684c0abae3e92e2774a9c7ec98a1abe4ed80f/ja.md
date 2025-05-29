```
t8_offset_any_owner_of_tree_ext(mpisize, start_proc, gtree, offset)
```

与えられたツリーをローカルツリーとして持つプロセスを見つけます。

# 引数

  * `mpisize`:[in] MPIランクの数、また*offset*のエントリ数から1を引いた数。
  * `start_proc`:[in] 検索を開始するmpirank。
  * `gtree`:[in] ツリーのグローバルID。
  * `offset`:[in] 考慮すべきパーティション。

# 戻り値

*gtree*をローカルツリーとして持つMPIランク。

### プロトタイプ

```c
int t8_offset_any_owner_of_tree_ext (const int mpisize, const int start_proc, const t8_gloidx_t gtree, const t8_gloidx_t *offset);
```
