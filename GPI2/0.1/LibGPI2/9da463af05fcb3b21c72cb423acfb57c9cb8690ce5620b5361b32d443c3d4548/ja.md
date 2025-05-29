```
gaspi_segment_ptr(segment_id, ptr)
```

指定されたセグメントの位置へのポインタを取得します。

### パラメータ

  * `segment_id`: セグメント識別子。
  * `ptr`: メモリセグメントへのポインタを持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_segment_ptr (const gaspi_segment_id_t segment_id, gaspi_pointer_t * ptr);
```
