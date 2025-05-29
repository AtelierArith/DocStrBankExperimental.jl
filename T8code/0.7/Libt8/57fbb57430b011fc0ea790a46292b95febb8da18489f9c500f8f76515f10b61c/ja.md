```
t8_netcdf_create_double_var(var_name, var_long_name, var_unit, var_data)
```

NetCDFファイルに出力される外部のdouble変数を作成します。

# 引数

  * `var_name`:[in] 作成される変数の名前となる文字列。
  * `var_long_name`:[in] 変数についてもう少し説明する文字列。
  * `var_unit`:[in] データが提供される単位。
  * `var_data`:[in] 変数の要素ごとのデータを保持する[`sc_array_t`](@ref)。
  * `num_extern_netcdf_vars`:[in] 要素ごとのデータを保持する外部ユーザー定義変数の数（ない場合は0に設定）。

### プロトタイプ

```c
t8_netcdf_variable_t * t8_netcdf_create_double_var (const char *var_name, const char *var_long_name, const char *var_unit, sc_array_t *var_data);
```
