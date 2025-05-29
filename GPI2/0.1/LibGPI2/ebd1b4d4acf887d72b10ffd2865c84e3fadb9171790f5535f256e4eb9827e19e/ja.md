```
gaspi_threads_get_tid(tid)
```

スレッド識別子を取得します

### パラメータ

  * `Output`: スレッド識別子を持つパラメータ

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERRORを返します。

### プロトタイプ

```c
gaspi_return_t gaspi_threads_get_tid(gaspi_int * const tid) __attribute__ ((deprecated));
```
