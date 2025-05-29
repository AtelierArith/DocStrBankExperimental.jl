```
t8_netcdf_create_integer_var(var_name, var_long_name, var_unit, var_data)
```

外部整数変数を作成します。この変数はNetCDFファイルに出力される必要があります（NC*INTまたはNC*INT64変数になるかどうかは、与えられた[`sc_array_t`](@ref)の要素サイズに基づきます）。

# 引数

  * `var_name`:[in] 作成される変数の名前となる文字列。
  * `var_long_name`:[in] 変数についてもう少し説明する文字列。
  * `var_unit`:[in] データが提供される単位。
  * `var_data`:[in] 変数の要素ごとのデータを保持する[`sc_array_t`](@ref)。
  * `num_extern_netcdf_vars`:[in] 要素ごとのデータを保持する外部ユーザー定義変数の数（ない場合は0に設定）。

### プロトタイプ

```c
t8_netcdf_variable_t * t8_netcdf_create_integer_var (const char *var_name, const char *var_long_name, const char *var_unit, sc_array_t *var_data);
```
