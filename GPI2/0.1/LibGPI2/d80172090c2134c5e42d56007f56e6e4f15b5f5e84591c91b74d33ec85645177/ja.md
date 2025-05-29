```
gaspi_statistic_counter_get(counter, argument, value)
```

統計カウンタを取得します。

### パラメータ

  * `counter`: 取得するカウンタ。
  * `argument`: カウンタの引数。
  * `value`: カウンタの現在の値を持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーの場合はGASPI*ERRORを返します。

### プロトタイプ

```c
gaspi_return_t gaspi_statistic_counter_get ( gaspi_statistic_counter_t counter, gaspi_number_t argument, unsigned long *value);
```
