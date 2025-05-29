```
gaspi_atomic_fetch_add(segment_id, offset, rank, val_add, val_old, timeout_ms)
```

原子フェッチ・アンド・アッド

!!! warning
    オフセットは8バイト境界に揃っている必要があります。


### パラメータ

  * `segment_id`: データが存在するセグメント識別子。
  * `offset`: データが存在するオフセット。
  * `rank`: 操作を実行するランク。
  * `val_add`: 加算する値。
  * `val_old`: 古い値（加算操作の前）の出力パラメータ。
  * `timeout_ms`: ミリ秒単位のタイムアウト（または GASPI*BLOCK/GASPI*TEST）。

### 戻り値

成功した場合は GASPI*SUCCESS、エラーの場合は GASPI*ERROR、タイムアウトの場合は GASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_atomic_fetch_add (const gaspi_segment_id_t segment_id, const gaspi_offset_t offset, const gaspi_rank_t rank, const gaspi_atomic_value_t val_add, gaspi_atomic_value_t * const val_old, const gaspi_timeout_t timeout_ms);
```
