```
gaspi_error_str(error_code)
```

戻り値を説明する文字列を取得します。これは、[`gaspi_print_error`](@ref) よりも少し実用的です。

### パラメータ

  * `error_code`: 説明される戻り値。

### 戻り値

戻り値を説明する文字列。

### プロトタイプ

```c
gaspi_string_t gaspi_error_str(gaspi_return_t error_code);
```
