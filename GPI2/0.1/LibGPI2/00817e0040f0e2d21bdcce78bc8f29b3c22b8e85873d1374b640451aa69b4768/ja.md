```
gaspi_allreduce_elem_max(elem_max)
```

[`gaspi_allreduce`](@ref)で許可される最大要素数を取得します。

### パラメータ

  * `elem_max`: 最大要素数を持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_allreduce_elem_max (gaspi_number_t * const elem_max);
```
