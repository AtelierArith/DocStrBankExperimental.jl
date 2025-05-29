```
dispatch_setup(model, attribute_name, modeldata, cellranges=modeldata.cellranges_all)
```

セットアップメソッドを呼び出します。例えば、データ配列（状態変数を含む）を初期化するためです。

`attribute_name` は実行されるセットアップ操作を定義します。`dispatch_setup` は次の `attribute_name` とともに順番に呼び出されるべきです：

  * `:setup`: 反応を初期化し、非状態変数（例えばモデルグリッド変数）を設定します（`modeldata` の `arrays_idx=1` に適用され、その後他の `arrays_idx` に値がコピーされます）
  * `:norm_value`: .yamlファイルの `:norm_value` 属性から状態変数の値を設定し、この値を必要とする反応状態を初期化します（`arrays_idx` 1 のみ）
  * `:initial_value`（オプション）: .yamlファイルの `:initial_value` 属性から状態変数の値を設定します（`arrays_idx` 1 のみ）
