```
gaspi_proc_term(timeout_ms)
```

シャットダウン手順。これは、リソースを解放し、必要なクリーンアップを行う同期的なローカル時間ベースのブロッキング操作です。

### パラメータ

  * `timeout_ms`: ミリ秒単位のタイムアウト（または GASPI*BLOCK/GASPI*TEST）。

### 戻り値

成功した場合は GASPI*SUCCESS、エラーが発生した場合は GASPI*ERROR、タイムアウトが発生した場合は GASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_proc_term (const gaspi_timeout_t timeout_ms);
```
