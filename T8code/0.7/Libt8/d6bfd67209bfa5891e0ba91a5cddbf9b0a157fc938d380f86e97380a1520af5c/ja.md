```
t8_offset_first(proc, offset)
```

指定されたプロセスの最初のローカルツリーのグローバルIDを返します。

# 引数

  * `proc`:[in] プロセスのランク。
  * `offset`:[in] パーティションテーブル。

# 戻り値

パーティション *offset* における *proc* の最初のローカルツリーのグローバルID。

### プロトタイプ

```c
t8_gloidx_t t8_offset_first (const int proc, const t8_gloidx_t *offset);
```
