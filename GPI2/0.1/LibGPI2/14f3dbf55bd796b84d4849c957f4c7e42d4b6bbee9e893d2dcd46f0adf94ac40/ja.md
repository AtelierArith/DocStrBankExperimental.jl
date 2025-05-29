```
gaspi_write_list_notify(num, segment_id_local, offset_local, rank, segment_id_remote, offset_remote, size, segment_id_notification, notification_id, notification_value, queue, timeout_ms)
```

異なる場所に書き込み、特定のランクに通知します。

### パラメータ

  * `num`: リスト内の要素数。
  * `segment_id_local`: データが存在するローカルセグメントのリスト。
  * `offset_local`: 書き込むデータが存在するローカルオフセットのリスト。
  * `rank`: リストと通知を書き込むランク。
  * `segment_id_remote`: 書き込むためのリモートセグメントのリスト。
  * `offset_remote`: 書き込むためのリモートオフセットのリスト。
  * `size`: 書き込むためのサイズのリスト。
  * `segment_id_notification`: 通知に使用されるセグメントID。
  * `notification_id`: 使用する通知識別子。
  * `notification_value`: 送信する通知値。
  * `queue`: リクエストを投稿するキュー。
  * `timeout_ms`: ミリ秒単位のタイムアウト（または GASPI*BLOCK/GASPI*TEST）。

### 戻り値

成功した場合は GASPI*SUCCESS、提供されたキューが満杯のためリクエストを投稿できなかった場合は GASPI*QUEUE*FULL、エラーが発生した場合は GASPI*ERROR、タイムアウトの場合は GASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_write_list_notify (const gaspi_number_t num, gaspi_segment_id_t * const segment_id_local, gaspi_offset_t * const offset_local, const gaspi_rank_t rank, gaspi_segment_id_t * const segment_id_remote, gaspi_offset_t * const offset_remote, gaspi_size_t * const size, const gaspi_segment_id_t segment_id_notification, const gaspi_notification_id_t notification_id, const gaspi_notification_t notification_value, const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
