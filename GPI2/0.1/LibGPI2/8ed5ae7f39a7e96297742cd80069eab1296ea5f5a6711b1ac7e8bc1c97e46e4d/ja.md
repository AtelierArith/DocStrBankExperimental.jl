```
gaspi_statistic_counter_info(counter, counter_argument, counter_name, counter_description, verbosity_level)
```

カウンタに関する情報を取得します。

### パラメータ

  * `counter`: カウンタ。
  * `counter_argument`: カウンタの意味を持つ出力パラメータ。
  * `counter_name`: カウンタの名前を持つ出力パラメータ。
  * `counter_description`: カウンタのより詳細な説明を持つ出力パラメータ。
  * `verbosity_level`: カウンタを有効にするための最小の冗長性レベルを持つ出力パラメータ。

### 戻り値

成功の場合はGASPI*SUCCESS、エラーの場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_statistic_counter_info( gaspi_statistic_counter_t counter, gaspi_statistic_argument_t* counter_argument, gaspi_string_t* counter_name, gaspi_string_t* counter_description, gaspi_number_t* verbosity_level);
```
