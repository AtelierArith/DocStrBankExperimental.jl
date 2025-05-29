```
gaspi_segment_size(segment_id, rank, size)
```

特定のランクにおける指定されたセグメントのサイズを取得します。

### パラメータ

  * `segment_id`: 我々が関心を持っているセグメントID。
  * `rank`: ランク。
  * `size`: セグメントのサイズを持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーの場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_segment_size (const gaspi_segment_id_t segment_id, const gaspi_rank_t rank, gaspi_size_t * const size);
```
