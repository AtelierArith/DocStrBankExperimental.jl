```
load_file_line_by_line(filename::AbstractString) -> String[]
```

テキストファイルの内容を `String[]` 形式で読み込み、返します。すなわち、各行に対して1つの要素があります。

# 引数

  * `filename::AbstractString`: 読み込むファイルのファイル名、

# キーワード

# 戻り値

  * `String[]`: ファイルの内容の配列、

# 例外

  * `Error`: ファイルが存在しない場合。
