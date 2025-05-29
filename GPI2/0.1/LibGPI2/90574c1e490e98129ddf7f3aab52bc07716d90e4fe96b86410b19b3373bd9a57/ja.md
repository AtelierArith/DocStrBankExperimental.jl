```
gaspi_allreduce_buf_size(buf_size)
```

[`gaspi_allreduce_user`](@ref) の内部バッファサイズを取得します。

### パラメータ

  * `buf_size`: バッファサイズを持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_allreduce_buf_size (gaspi_size_t * const buf_size);
```
