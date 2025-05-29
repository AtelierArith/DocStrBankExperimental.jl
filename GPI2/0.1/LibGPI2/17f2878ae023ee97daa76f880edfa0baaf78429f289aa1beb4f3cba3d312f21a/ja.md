```
gaspi_passive_send(segment_id_local, offset_local, rank, size, timeout_ms)
```

指定されたサイズのデータを指定されたランクに送信します。

### パラメータ

  * `segment_id_local`: ローカルセグメント識別子。
  * `offset_local`: 送信するデータがあるオフセット。
  * `rank`: 送信先のランク。
  * `size`: 送信するデータのサイズ。
  * `timeout_ms`: ミリ秒単位のタイムアウト（または GASPI*BLOCK/GASPI*TEST）。

### 戻り値

成功した場合は GASPI*SUCCESS、エラーの場合は GASPI*ERROR、タイムアウトの場合は GASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_passive_send (const gaspi_segment_id_t segment_id_local, const gaspi_offset_t offset_local, const gaspi_rank_t rank, const gaspi_size_t size, const gaspi_timeout_t timeout_ms);
```
