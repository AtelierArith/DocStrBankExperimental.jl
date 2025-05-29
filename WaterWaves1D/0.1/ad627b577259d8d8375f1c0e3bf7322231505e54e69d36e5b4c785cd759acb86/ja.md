```
load_init(file_name :: String; fast = false)
```

ファイル名 `file_name`（拡張子 ".h5"）から初期データをロードします。

キーワード引数 `fast` はオプション（デフォルトは `false`）で、関数 `Init` のキーワード引数に対応します。

`InitialData` 型のオブジェクトを返します。
