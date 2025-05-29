```
gaspi_threads_run(_function, arg)
```

特定のタスク（関数）を実行します。

### パラメータ

  * `function`: 実行する関数。
  * `arg`: 実行する関数の引数。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_threads_run(void* (*function)(void*), void *arg) __attribute__ ((deprecated));
```
