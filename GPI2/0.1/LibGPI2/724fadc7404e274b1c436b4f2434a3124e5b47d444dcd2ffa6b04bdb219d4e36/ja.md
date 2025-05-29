```
gaspi_segment_alloc(segment_id, size, alloc_policy)
```

セグメントを割り当てます。

### パラメータ

  * `segment_id`: 作成されるセグメントの識別子。
  * `size`: 作成されるセグメントのサイズ。
  * `alloc_policy`: 割り当てポリシー。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_segment_alloc (const gaspi_segment_id_t segment_id, const gaspi_size_t size, const gaspi_alloc_t alloc_policy);
```
