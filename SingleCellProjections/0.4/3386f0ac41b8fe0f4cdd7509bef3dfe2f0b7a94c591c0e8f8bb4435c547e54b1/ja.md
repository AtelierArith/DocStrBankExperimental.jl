```
set_obs_id_col!(data::DataMatrix, obs_id_col::String; duplicate_obs=:error)
```

観察IDとして使用する列を設定します。この列は`data.obs`の最初の列に移動されます。この列の行は`data.obs`内で一意でなければなりません。

  * `duplicate_obs` - 重複IDが見つかった場合にどうするかを決定するために、:ignore、:warn、または:errorに設定します。
