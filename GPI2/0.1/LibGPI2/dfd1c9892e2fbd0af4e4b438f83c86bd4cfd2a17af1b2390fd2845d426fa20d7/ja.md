```
gaspi_atomic_max(max_value)
```

[`gaspi_atomic_value_t`](@ref) が保持できる最大値。

### パラメータ

  * `max_value`: 原子操作に対して許可される最大値を持つ出力パラメータ。

### 戻り値

成功した場合は GASPI*SUCCESS、エラーが発生した場合は GASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_atomic_max(gaspi_atomic_value_t *max_value);
```
