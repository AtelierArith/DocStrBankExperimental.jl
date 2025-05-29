```
gaspi_segment_use(segment_id, pointer, size, group, timeout, memory_description)
```

ユーザー提供のバッファをセグメントとして使用します。

### パラメータ

  * `segment_id`: 使用するセグメント識別子。
  * `pointer`: 使用するバッファアドレス。
  * `size`: セグメントのサイズ。
  * `group`: 操作に参加するグループ。
  * `timeout`: 操作のタイムアウト（ミリ秒単位）。
  * `memory_description`: 使用するメモリの説明。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR、タイムアウトが発生した場合はGASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_segment_use (gaspi_segment_id_t const segment_id, gaspi_pointer_t const pointer, gaspi_size_t const size, gaspi_group_t const group, gaspi_timeout_t const timeout, gaspi_memory_description_t const memory_description);
```
