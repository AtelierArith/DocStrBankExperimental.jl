```
gaspi_threads_get_num_cores(cores)
```

利用可能なCPUコアの総数を取得します。

### パラメータ

  * `cores`: コアの数を持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_threads_get_num_cores(gaspi_int * const cores) __attribute__ ((deprecated));
```
