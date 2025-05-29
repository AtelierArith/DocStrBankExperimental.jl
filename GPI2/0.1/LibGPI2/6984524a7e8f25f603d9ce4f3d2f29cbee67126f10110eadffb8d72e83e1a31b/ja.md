```
gaspi_segment_register(segment_id, rank, timeout_ms)
```

通信のためのセグメントを登録します。成功した場合、セグメントは関与するランク間の通信に使用できます。

### パラメータ

  * `segment_id`: 登録されるセグメントの識別子。
  * `rank`: このセグメントを登録するランク。
  * `timeout_ms`: ミリ秒単位のタイムアウト（または GASPI*BLOCK/GASPI*TEST）。

### 戻り値

成功した場合は GASPI*SUCCESS、エラーの場合は GASPI*ERROR、タイムアウトの場合は GASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_segment_register (const gaspi_segment_id_t segment_id, const gaspi_rank_t rank, const gaspi_timeout_t timeout_ms);
```
