```
gaspi_wait(queue, timeout_ms)
```

指定されたキューに投稿されたリクエストを待機します。

### パラメータ

  * `queue`: 待機するキュー。
  * `timeout_ms`: ミリ秒単位のタイムアウト（または GASPI*BLOCK/GASPI*TEST）。

### 戻り値

成功した場合は GASPI*SUCCESS、エラーが発生した場合は GASPI*ERROR、タイムアウトが発生した場合は GASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_wait (const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
