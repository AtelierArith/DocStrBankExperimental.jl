```
gaspi_threads_register(tid)
```

プールにスレッドを登録します。

### パラメータ

  * `tid`: スレッド識別子を持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_threads_register(gaspi_int * tid);
```
