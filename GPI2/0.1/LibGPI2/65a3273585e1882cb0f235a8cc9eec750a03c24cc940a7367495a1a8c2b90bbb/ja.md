```
gaspi_threads_get_total(num)
```

スレッドの総数を取得します

### パラメータ

  * `Output`: スレッドの総数を持つパラメータ

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERRORを返します。

### プロトタイプ

```c
gaspi_return_t gaspi_threads_get_total(gaspi_int *const num) __attribute__ ((deprecated));
```
