```
gaspi_time_get(wtime)
```

経過時間を取得します（ミリ秒単位）。

### パラメータ

  * `wtime`: ミリ秒単位の時間を持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_time_get (gaspi_time_t * const wtime);
```
