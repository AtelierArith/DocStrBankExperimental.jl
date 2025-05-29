```
gaspi_segment_bind(segment_id, pointer, size, memory_description)
```

ユーザー提供のバッファをセグメントとして使用します。

### パラメータ

  * `segment_id`: 使用するセグメント識別子。
  * `pointer`: 使用するバッファアドレス。
  * `size`: セグメントのサイズ。
  * `memory_description`: 使用するメモリの説明。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーの場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_segment_bind (gaspi_segment_id_t const segment_id, gaspi_pointer_t const pointer, gaspi_size_t const size, gaspi_memory_description_t const memory_description);
```
