```
exportCSV(author::TCXAuthor, activities::Vector{TCXActivity}, csv_filepath::String)
```

解析されたTCXデータをCSVファイルにエクスポートします。

# 引数

  * `author`: 著者情報を含む`TCXAuthor`オブジェクト。
  * `activities`: アクティビティを表す`TCXActivity`オブジェクトのベクター。
  * `csv_filepath`: CSVファイルが保存されるファイルパス。
