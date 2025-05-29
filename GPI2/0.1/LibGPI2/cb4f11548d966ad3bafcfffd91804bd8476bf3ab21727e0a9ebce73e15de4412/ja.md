```
gaspi_statistic_counter_reset(counter)
```

カウンターをリセットします（0に設定）。

### パラメータ

  * `counter`: リセットするカウンター。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーの場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_statistic_counter_reset (gaspi_statistic_counter_t counter);
```
