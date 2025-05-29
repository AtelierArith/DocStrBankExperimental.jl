```
t8_netcdf_create_var(var_type, var_name, var_long_name, var_unit, var_data)
```

NetCDFファイルに出力される外部のdouble変数を作成します。

# 引数

  * `var_type`:[in] 変数のデータ型を定義します。T8*NETCDF*INT、T8*NETCDF*INT64、またはT8*NETCDF*DOUBLEのいずれかです。
  * `var_name`:[in] 作成される変数の名前となる文字列です。
  * `var_long_name`:[in] 変数についてもう少し説明する文字列です。
  * `var_unit`:[in] データが提供される単位です。
  * `var_data`:[in] 変数の要素ごとのデータを保持する[`sc_array_t`](@ref)です。
  * `num_extern_netcdf_vars`:[in] 要素ごとのデータを保持する外部のユーザー定義変数の数（ない場合は0に設定します）。

### プロトタイプ

```c
t8_netcdf_variable_t * t8_netcdf_create_var (t8_netcdf_variable_type_t var_type, const char *var_name, const char *var_long_name, const char *var_unit, sc_array_t *var_data);
```
