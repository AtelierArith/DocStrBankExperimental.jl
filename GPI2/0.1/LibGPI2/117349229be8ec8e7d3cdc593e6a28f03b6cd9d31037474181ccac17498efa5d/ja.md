```
gaspi_proc_kill(rank, timeout_ms)
```

指定されたプロセス（ランク）を終了します。

### パラメータ

  * `rank`: 終了するランク。
  * `timeout_ms`: ミリ秒単位のタイムアウト（または GASPI*BLOCK/GASPI*TEST）。

### 戻り値

成功した場合は GASPI*SUCCESS、エラーの場合は GASPI*ERROR、タイムアウトの場合は GASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_proc_kill (const gaspi_rank_t rank, const gaspi_timeout_t timeout_ms);
```
