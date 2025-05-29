```
@savefile(filename, arr, kwargs...)
```

配列または配列のタプル `arr` をファイル `filename` に `EC.scr` ディレクトリに保存します。

# キーワード引数

  * `description::String`: ファイルの説明 (デフォルト: "tmp")。
  * `overwrite::Bool`: 既存のファイルを上書きする (デフォルト: `false`)。
