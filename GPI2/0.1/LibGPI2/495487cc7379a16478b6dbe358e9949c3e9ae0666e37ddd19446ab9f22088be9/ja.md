```
gaspi_write_list(num, segment_id_local, offset_local, rank, segment_id_remote, offset_remote, size, queue, timeout_ms)
```

書き込みリスト。

### パラメータ

  * `num`: リスト要素の数（[`gaspi_rw_list_elem_max`](@ref)も参照）
  * `segment_id_local`: 書き込むデータを持つローカルセグメントのリスト。
  * `offset_local`: 書き込むデータを持つローカルオフセットのリスト。
  * `rank`: 書き込む先のランク。
  * `segment_id_remote`: 書き込むリモートセグメントのリスト。
  * `offset_remote`: 書き込むリモートオフセットのリスト。
  * `size`: 書き込むサイズのリスト。
  * `queue`: リストを投稿するキュー。
  * `timeout_ms`: ミリ秒単位のタイムアウト（またはGASPI*BLOCK/GASPI*TEST）。

### 戻り値

成功した場合はGASPI*SUCCESS、提供されたキューが満杯のためにリクエストを投稿できなかった場合はGASPI*QUEUE*FULL、エラーが発生した場合はGASPI*ERROR、タイムアウトが発生した場合はGASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_write_list (const gaspi_number_t num, gaspi_segment_id_t * const segment_id_local, gaspi_offset_t * const offset_local, const gaspi_rank_t rank, gaspi_segment_id_t * const segment_id_remote, gaspi_offset_t * const offset_remote, gaspi_size_t * const size, const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
