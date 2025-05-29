```
gaspi_notify(segment_id_remote, rank, notification_id, notification_value, queue, timeout_ms)
```

特定の値を指定されたランクに通知します。

### パラメータ

  * `segment_id_remote`: リモートセグメントID。
  * `rank`: 通知するランク。
  * `notification_id`: 通知ID。
  * `notification_value`: 通知値。
  * `queue`: 通知リクエストを投稿するキュー。
  * `timeout_ms`: ミリ秒単位のタイムアウト（または GASPI*BLOCK/GASPI*TEST）。

### 戻り値

成功した場合は GASPI*SUCCESS、エラーの場合は GASPI*ERROR、タイムアウトの場合は GASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_notify (const gaspi_segment_id_t segment_id_remote, const gaspi_rank_t rank, const gaspi_notification_id_t notification_id, const gaspi_notification_t notification_value, const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
