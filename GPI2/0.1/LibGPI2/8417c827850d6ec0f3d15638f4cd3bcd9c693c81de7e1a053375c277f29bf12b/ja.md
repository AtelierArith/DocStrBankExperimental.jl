```
gaspi_write(segment_id_local, offset_local, rank, segment_id_remote, offset_remote, size, queue, timeout_ms)
```

片方向書き込み。

### パラメータ

  * `segment_id_local`: 書き込むデータを持つローカルセグメントID。
  * `offset_local`: 書き込むデータのローカルオフセット。
  * `rank`: 書き込みたいランク。
  * `segment_id_remote`: 書き込むリモートセグメントID。
  * `offset_remote`: 書き込むリモートオフセット。
  * `size`: 書き込むデータのサイズ。
  * `queue`: 書き込みリクエストを投稿するキュー。
  * `timeout_ms`: ミリ秒単位のタイムアウト（または GASPI*BLOCK/GASPI*TEST）。

### 戻り値

成功した場合は GASPI*SUCCESS、提供されたキューが満杯のためリクエストを投稿できなかった場合は GASPI*QUEUE*FULL、エラーが発生した場合は GASPI*ERROR、タイムアウトの場合は GASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_write (const gaspi_segment_id_t segment_id_local, const gaspi_offset_t offset_local, const gaspi_rank_t rank, const gaspi_segment_id_t segment_id_remote, const gaspi_offset_t offset_remote, const gaspi_size_t size, const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
