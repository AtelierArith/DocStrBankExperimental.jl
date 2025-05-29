```
gaspi_passive_receive(segment_id_local, offset_local, rem_rank, size, timeout_ms)
```

指定されたサイズのデータを任意のランクから受信します。

### パラメータ

  * `segment_id_local`: 受信したデータを配置するセグメント。
  * `offset_local`: 受信したデータを配置するローカルオフセット。
  * `rem_rank`: 送信者（ランク）を含む出力パラメータ。
  * `size`: 受信するサイズ。
  * `timeout_ms`: ミリ秒単位のタイムアウト（または GASPI*BLOCK/GASPI*TEST）。

### 戻り値

成功した場合は GASPI*SUCCESS、エラーの場合は GASPI*ERROR、タイムアウトの場合は GASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_passive_receive (const gaspi_segment_id_t segment_id_local, const gaspi_offset_t offset_local, gaspi_rank_t * const rem_rank, const gaspi_size_t size, const gaspi_timeout_t timeout_ms);
```
