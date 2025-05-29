```
set_var_id_col!(data::DataMatrix, var_id_col::String; duplicate_var=:error)
```

変数IDとして使用する列を設定します。この列は`data.var`の最初の列に移動されます。この列の行は`data.var`内で一意でなければなりません。

  * `duplicate_var` - 重複IDが見つかった場合に何が起こるかを決定するために、:ignore、:warn、または:errorに設定します。
