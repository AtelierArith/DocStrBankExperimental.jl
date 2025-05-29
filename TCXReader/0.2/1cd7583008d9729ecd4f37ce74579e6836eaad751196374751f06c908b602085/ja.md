```
loadTCXFile(filepath::String, csv_filepath::Union{String,Nothing}=nothing)
```

TCXファイルを読み込み、その内容を解析します。

# 引数

  * `filepath`: TCXファイルへのパス。
  * `csv_filepath`: オプション。提供された場合、解析されたデータはこのCSVファイルにエクスポートされます。

# 戻り値

  * 解析された `TCXAuthor` と `TCXActivity` オブジェクトのベクターを含むタプル。
