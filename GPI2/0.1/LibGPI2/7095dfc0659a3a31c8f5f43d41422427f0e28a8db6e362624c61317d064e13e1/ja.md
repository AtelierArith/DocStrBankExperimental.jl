```
gaspi_threads_init_user(use_nr_of_threads)
```

スレッドを初期化します（特定の数のスレッド）

### パラメータ

  * `use_nr_of_threads`: 開始するスレッドの数。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_threads_init_user(const unsigned int use_nr_of_threads) __attribute__ ((deprecated));
```
