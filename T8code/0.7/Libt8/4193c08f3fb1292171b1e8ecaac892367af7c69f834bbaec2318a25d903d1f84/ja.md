```
t8_offset_empty(proc, offset)
```

指定されたプロセスが特定のパーティションにローカルツリーを持たないかどうかを確認します。

# 引数

  * `proc`:[in] MPIランク。
  * `offset`:[in] パーティションテーブル。

# 戻り値

*proc* が *offset* にローカルツリーを持たない場合は非ゼロ。そうでない場合は0。

### プロトタイプ

```c
int t8_offset_empty (const int proc, const t8_gloidx_t *offset);
```
