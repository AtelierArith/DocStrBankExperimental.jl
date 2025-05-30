```
t8_offset_last_owner_of_tree(mpisize, gtree, offset, some_owner)
```

与えられたツリーをローカルツリーとして持つ最大のプロセスを見つけます。実行時間を増加させるために、このツリーをローカルツリーとして持つ任意のプロセスを引数として渡すことができます。そうでない場合、そのようなオーナーは呼び出し中に計算されます。

# 引数

  * `mpisize`:[in] MPIランクの数、また*offset*のエントリ数から1を引いた数。
  * `gtree`:[in] ツリーのグローバルID。
  * `offset`:[in] 考慮すべきパーティション。
  * `some_owner`:[in,out] >= 0の場合は入力として考慮される: *gtree*をローカルツリーとして持つプロセス。< 0の場合は出力として*gtree*をローカルツリーとして持つプロセス。*some_owner*を指定すると、実行時間がO(log mpisize)からO(n)に増加します。ここで、nはツリーのオーナーの数です。

# 戻り値

*gtree*をローカルツリーとして持つ最大のランク。

### プロトタイプ

```c
int t8_offset_last_owner_of_tree (const int mpisize, const t8_gloidx_t gtree, const t8_gloidx_t *offset, int *some_owner);
```
