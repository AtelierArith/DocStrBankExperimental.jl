```
data = fld_read(file::String ; dir::String="", chat=false)
```

AVS形式の`.fld`ファイルからデータを読み取ります

引数

  * `file` ファイル名、通常は`.fld`で終わります

オプション

  * `dir::String` ファイル名の前にこのディレクトリを付加します; デフォルトは""
  * `chat::Bool` 詳細表示しますか？

出力

  * `data` ファイル自体のデータ型の配列 (1D - 5D)
