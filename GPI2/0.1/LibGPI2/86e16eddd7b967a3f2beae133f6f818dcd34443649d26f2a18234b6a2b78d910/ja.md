```
gaspi_read_list(num, segment_id_local, offset_local, rank, segment_id_remote, offset_remote, size, queue, timeout_ms)
```

読み取りリスト。

### パラメータ

  * `num`: リスト要素の数。
  * `segment_id_local`: データが配置されるローカルセグメントのリスト。
  * `offset_local`: データが配置されるローカルオフセットのリスト。
  * `rank`: 読み取るランク。
  * `segment_id_remote`: 読み取るリモートセグメントのリスト。
  * `offset_remote`: 読み取るリモートオフセットのリスト。
  * `size`: 読み取るサイズのリスト。
  * `queue`: リストを投稿するキュー。
  * `timeout_ms`: ミリ秒単位のタイムアウト（または GASPI*BLOCK/GASPI*TEST）。

### 戻り値

成功した場合は GASPI*SUCCESS、提供されたキューが満杯のために要求を投稿できなかった場合は GASPI*QUEUE*FULL、エラーが発生した場合は GASPI*ERROR、タイムアウトの場合は GASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_read_list (const gaspi_number_t num, gaspi_segment_id_t * const segment_id_local, gaspi_offset_t * const offset_local, const gaspi_rank_t rank, gaspi_segment_id_t * const segment_id_remote, gaspi_offset_t * const offset_remote, gaspi_size_t * const size, const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
