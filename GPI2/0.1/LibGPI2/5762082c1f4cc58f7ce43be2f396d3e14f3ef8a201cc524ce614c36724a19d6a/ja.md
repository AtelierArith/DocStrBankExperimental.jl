```
gaspi_write_notify(segment_id_local, offset_local, rank, segment_id_remote, offset_remote, size, notification_id, notification_value, queue, timeout_ms)
```

指定されたノードにデータを書き込み、通知します。

### パラメータ

  * `segment_id_local`: 書き込むデータがあるセグメントの識別子。
  * `offset_local`: 書き込むデータがあるオフセット。
  * `rank`: 書き込みと通知を行うランク。
  * `segment_id_remote`: データを書き込むリモートセグメントの識別子。
  * `offset_remote`: 書き込むリモートオフセット。
  * `size`: 書き込むデータのサイズ。
  * `notification_id`: 使用する通知の識別子。
  * `notification_value`: 使用される通知の値。
  * `queue`: リクエストを投稿するキュー。
  * `timeout_ms`: ミリ秒単位のタイムアウト（または GASPI*BLOCK/GASPI*TEST）。

### 戻り値

成功した場合は GASPI*SUCCESS、提供されたキューが満杯のためリクエストを投稿できなかった場合は GASPI*QUEUE*FULL、エラーが発生した場合は GASPI*ERROR、タイムアウトの場合は GASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_write_notify (const gaspi_segment_id_t segment_id_local, const gaspi_offset_t offset_local, const gaspi_rank_t rank, const gaspi_segment_id_t segment_id_remote, const gaspi_offset_t offset_remote, const gaspi_size_t size, const gaspi_notification_id_t notification_id, const gaspi_notification_t notification_value, const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
