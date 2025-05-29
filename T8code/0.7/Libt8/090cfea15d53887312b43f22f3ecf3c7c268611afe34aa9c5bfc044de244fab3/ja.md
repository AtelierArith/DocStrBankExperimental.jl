```
t8_offset_first_owner_of_tree(mpisize, gtree, offset, some_owner)
```

与えられた木をローカルツリーとして持つ最小のプロセスを見つけます。実行時間を増加させるために、この木をローカルツリーとして持つ任意のプロセスを引数として渡すことができます。そうでない場合、そのようなオーナーは呼び出し中に計算されます。

# 引数

  * `mpisize`:[in] MPIランクの数、また*offset*のエントリ数から1を引いた数。
  * `gtree`:[in] 木のグローバルID。
  * `offset`:[in] 考慮すべきパーティション。
  * `some_owner`:[in] >= 0の場合は入力として考慮される: *gtree*をローカルツリーとして持つプロセス。< 0の場合は出力として*gtree*をローカルツリーとして持つプロセス。*some_owner*を指定すると、実行時間がO(log mpisize)からO(n)に増加します。ここで、nは木のオーナーの数です。

# 戻り値

*gtree*をローカルツリーとして持つ最小のランク。

### プロトタイプ

```c
int t8_offset_first_owner_of_tree (const int mpisize, const t8_gloidx_t gtree, const t8_gloidx_t *offset, int *some_owner);
```
