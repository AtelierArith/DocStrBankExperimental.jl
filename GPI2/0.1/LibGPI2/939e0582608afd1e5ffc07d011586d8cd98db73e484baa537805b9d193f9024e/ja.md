```
gaspi_threads_init(num)
```

スレッドを初期化します（利用可能なすべてのコアで）

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_threads_init(gaspi_int * const num) __attribute__ ((deprecated));
```
