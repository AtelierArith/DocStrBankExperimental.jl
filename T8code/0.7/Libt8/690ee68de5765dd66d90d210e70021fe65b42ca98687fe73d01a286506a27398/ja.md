```
t8_offset_last(proc, offset)
```

指定されたプロセスの最後のローカルツリーをパーティション内で返します。

# 引数

  * `proc`:[in] MPIランク。
  * `offset`:[in] パーティションテーブル。

# 戻り値

*proc*の最後のローカルツリーのグローバルツリーIDを*offset*内で返します。

### プロトタイプ

```c
t8_gloidx_t t8_offset_last (const int proc, const t8_gloidx_t *offset);
```
