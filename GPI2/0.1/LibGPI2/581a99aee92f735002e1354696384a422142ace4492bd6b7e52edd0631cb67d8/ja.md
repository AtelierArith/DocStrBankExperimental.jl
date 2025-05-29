```
gaspi_barrier(group, timeout_ms)
```

バリア。

### パラメータ

  * `group`: バリアに関与するグループ。
  * `timeout_ms`: ミリ秒単位のタイムアウト（または GASPI*BLOCK/GASPI*TEST）。

### 戻り値

成功した場合は GASPI*SUCCESS、エラーが発生した場合は GASPI*ERROR、タイムアウトの場合は GASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_barrier (const gaspi_group_t group, const gaspi_timeout_t timeout_ms);
```
