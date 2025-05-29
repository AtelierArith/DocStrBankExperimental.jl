```
gaspi_atomic_compare_swap(segment_id, offset, rank, comparator, val_new, val_old, timeout_ms)
```

原子比較交換。

### パラメータ

  * `segment_id`: データのセグメント識別子。
  * `offset`: データのオフセット。
  * `rank`: 操作を実行するランク。
  * `comparator`: 操作の比較値。
  * `val_new`: 比較が成功した場合に交換する新しい値。
  * `val_old`: 古い値（操作前）の出力パラメータ。
  * `timeout_ms`: ミリ秒単位のタイムアウト（または GASPI*BLOCK/GASPI*TEST）。

### 戻り値

成功した場合は GASPI*SUCCESS、エラーの場合は GASPI*ERROR、タイムアウトの場合は GASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_atomic_compare_swap (const gaspi_segment_id_t segment_id, const gaspi_offset_t offset, const gaspi_rank_t rank, const gaspi_atomic_value_t comparator, const gaspi_atomic_value_t val_new, gaspi_atomic_value_t * const val_old, const gaspi_timeout_t timeout_ms);
```
