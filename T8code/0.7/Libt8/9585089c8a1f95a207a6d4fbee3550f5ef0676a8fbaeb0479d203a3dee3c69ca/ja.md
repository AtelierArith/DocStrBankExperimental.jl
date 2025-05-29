```
t8_offset_nosend(proc, mpisize, offset_from, offset_to)
```

与えられたプロセスが他のプロセス（自分自身を含む）にローカルツリーを送信するかどうかを再分配設定で照会します。

# 引数

  * `proc`:[in] MPIランク。
  * `mpisize`:[in] MPIランクの数、また*offset*のエントリ数から1を引いた数。
  * `offset_from`:[in] 現在のパーティションのパーティションテーブル。
  * `offset_to`:[in] 次のパーティションのパーティションテーブル。

# 戻り値

*proc*が*offset_from*から*offset_to*に再分配する場合、ローカルツリーを送信しない場合は非ゼロ、送信する場合は0。

### プロトタイプ

```c
int t8_offset_nosend (int proc, int mpisize, const t8_gloidx_t *offset_from, const t8_gloidx_t *offset_to);
```
