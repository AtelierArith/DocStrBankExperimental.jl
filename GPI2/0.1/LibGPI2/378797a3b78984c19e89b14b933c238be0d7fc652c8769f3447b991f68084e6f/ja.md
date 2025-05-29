```
gaspi_allreduce(buffer_send, buffer_receive, num, operation, datatype, group, timeout_ms)
```

全体集約の集団操作。

### パラメータ

  * `buffer_send`: 操作のためのデータを含むバッファ。
  * `buffer_receive`: 操作の結果を受け取るためのバッファ。
  * `num`: バッファ内のデータ要素の数（最大に注意 - [`gaspi_allreduce_elem_max`](@ref)を使用）。
  * `operation`: 操作の種類（[`gaspi_operation_t`](@ref)を参照）。
  * `datatyp`: データの型（[`gaspi_datatype_t`](@ref)を参照）。
  * `group`: 操作に関与するグループ。
  * `timeout_ms`: ミリ秒単位のタイムアウト（またはGASPI*BLOCK/GASPI*TEST）。

### 戻り値

成功の場合はGASPI*SUCCESS、エラーの場合はGASPI*ERROR、タイムアウトの場合はGASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_allreduce (const gaspi_pointer_t buffer_send, gaspi_pointer_t const buffer_receive, const gaspi_number_t num, const gaspi_operation_t operation, const gaspi_datatype_t datatype, const gaspi_group_t group, const gaspi_timeout_t timeout_ms);
```
