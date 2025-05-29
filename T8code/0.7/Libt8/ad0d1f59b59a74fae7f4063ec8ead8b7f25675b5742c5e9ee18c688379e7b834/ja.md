```
t8_offset_num_trees(proc, offset)
```

与えられたプロセスのパーティション内の木の数。

# 引数

  * `proc`:[in] MPIランク。
  * `offset`:[in] パーティションテーブル。

# 戻り値

パーティション*offset*内の*proc*のローカル木の数。

### プロトタイプ

```c
t8_gloidx_t t8_offset_num_trees (const int proc, const t8_gloidx_t *offset);
```
