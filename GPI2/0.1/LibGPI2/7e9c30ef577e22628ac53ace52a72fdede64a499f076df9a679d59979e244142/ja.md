```
gaspi_statistic_counter_max(counter_max)
```

統計カウンタの最大数を取得します。

### パラメータ

  * `counter_max`: カウンタの最大数を持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERRORを返します。

### プロトタイプ

```c
gaspi_return_t gaspi_statistic_counter_max(gaspi_number_t* counter_max);
```
