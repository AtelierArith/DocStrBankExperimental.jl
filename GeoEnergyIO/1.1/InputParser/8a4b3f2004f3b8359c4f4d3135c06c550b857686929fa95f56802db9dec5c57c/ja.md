```
parse_grdecl_file("mygrid.grdecl"; actnum_path = missing, kwarg...)
```

GRDECLファイルをフル入力ファイルとは別に解析します。GRIDセクションには単位が含まれていないため、`input_units`キーワードを渡すことを強く推奨します。

# キーワード引数

  * `actnum_path=missing`: メインファイルに含まれていない場合のACTNUMファイルへのパス。
  * `units=:si`: 戻り値に使用する単位。`input_units`を設定する必要があります。
  * `input_units=nothing`: ファイルが与えられている単位。
  * `verbose=false`: 詳細表示の切り替え。
  * `extra_paths`: グリッドセクションの一部として解析する追加パスのリスト、例: `["PORO.inc", "PERM.inc"]`。
