```
gaspi_read(segment_id_local, offset_local, rank, segment_id_remote, offset_remote, size, queue, timeout_ms)
```

片方向の読み取り。

### パラメータ

  * `segment_id_local`: データが配置されるローカルセグメントID。
  * `offset_local`: データが配置されるローカルオフセット。
  * `rank`: 読み取りたいランク。
  * `segment_id_remote`: 読み取るリモートセグメントID。
  * `offset_remote`: 読み取るリモートオフセット。
  * `size`: 読み取るデータのサイズ。
  * `queue`: 読み取り要求を投稿するキュー。
  * `timeout_ms`: ミリ秒単位のタイムアウト（または GASPI*BLOCK/GASPI*TEST）。

### 戻り値

成功した場合は GASPI*SUCCESS、提供されたキューが満杯のため要求を投稿できなかった場合は GASPI*QUEUE*FULL、エラーが発生した場合は GASPI*ERROR、タイムアウトの場合は GASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_read (const gaspi_segment_id_t segment_id_local, const gaspi_offset_t offset_local, const gaspi_rank_t rank, const gaspi_segment_id_t segment_id_remote, const gaspi_offset_t offset_remote, const gaspi_size_t size, const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
