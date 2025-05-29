```
gaspi_segment_create(segment_id, size, group, timeout_ms, alloc_policy)
```

セグメントを作成します。これは、指定されたグループのすべてのメンバーを含む、`gaspi_segment_alloc`、[`gaspi_segment_register`](@ref) および [`gaspi_barrier`](@ref) の集合的な集約と意味的に同等です。

### パラメータ

  * `segment_id`: セグメントを識別するためのセグメントID。
  * `size`: セグメントのサイズ（バイト単位）。
  * `group`: セグメントを登録するランクのグループ。
  * `timeout_ms`: ミリ秒単位のタイムアウト（または GASPI*BLOCK/GASPI*TEST）。
  * `alloc_policy`: メモリ割り当てポリシー。

### 戻り値

成功した場合は GASPI*SUCCESS、エラーの場合は GASPI*ERROR、タイムアウトの場合は GASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_segment_create (const gaspi_segment_id_t segment_id, const gaspi_size_t size, const gaspi_group_t group, const gaspi_timeout_t timeout_ms, const gaspi_alloc_t alloc_policy);
```
