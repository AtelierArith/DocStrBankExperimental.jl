```
gaspi_notify_waitsome(segment_id_local, notification_begin, num, first_id, timeout_ms)
```

いくつかの通知を待ちます。

### パラメータ

  * `segment_id_local`: セグメント識別子。
  * `notification_begin`: 待機を開始する通知ID。
  * `num`: 待機する通知の数。
  * `first_id`: 受信した通知の識別子を持つ出力パラメータ。
  * `timeout_ms`: ミリ秒単位のタイムアウト（または GASPI*BLOCK/GASPI*TEST）。

### 戻り値

成功した場合は GASPI*SUCCESS、エラーの場合は GASPI*ERROR、タイムアウトの場合は GASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_notify_waitsome (const gaspi_segment_id_t segment_id_local, const gaspi_notification_id_t notification_begin, const gaspi_number_t num, gaspi_notification_id_t * const first_id, const gaspi_timeout_t timeout_ms);
```
