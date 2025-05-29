```
set_statevar_from_output!(modeldata, output::AbstractOutputWriter) -> initial_state
```

出力の最後のレコードからモデルの状態変数を初期化します。

注: `modeldata` は `solver_view_all` を含む必要があります。
